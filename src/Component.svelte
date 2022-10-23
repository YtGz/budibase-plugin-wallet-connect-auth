<script>
  import { getContext } from 'svelte'
  import { Button } from '@budibase/bbui'
  import { AuthClient, generateNonce } from '@walletconnect/auth-client'
  import QRCodeModal from '@walletconnect/qrcode-modal'

  const { styleable, Provider } = getContext('sdk')
  const component = getContext('component')

  export let walletConnectCloudProjectId
  export let dAppName
  export let dAppDescription = ''
  export let dAppDomain
  export let dAppUrl
  export let dAppIcon = ''
  export let dAppChainId = 'eip155:1'

  let isAuthenticated = false
  $: dataContext = {
    isAuthenticated
  }

  const authClientPromise = AuthClient.init({
    projectId: walletConnectCloudProjectId,
    metadata: {
      name: dAppName,
      description: dAppDescription,
      url: dAppUrl,
      icons: [dAppIcon]
    }
  })

  const authenticate = async () => {
    const authClient = await authClientPromise
    const nonce = generateNonce()
    const { uri } =
      (await authClient.request({
        aud: dAppUrl,
        domain: dAppDomain,
        chainId: dAppChainId,
        nonce: nonce
      })) ?? undefined

    if (uri !== undefined) {
      QRCodeModal.open(uri)
    }

    authClient.on('auth_response', ({ params }) => {
      if (Boolean(params.result?.s)) {
        // Response contained a valid signature -> user is authenticated.
        console.log('Authentication successful.')
        isAuthenticated = true
        QRCodeModal.close()
      } else {
        // Handle error or invalid signature case
        console.error(params.message)
      }
    })
  }
</script>

<div use:styleable={$component.styles}>
  {#if !isAuthenticated}
    {#await authClientPromise}
      <Button primary={true} disabled={true}>Connect Wallet</Button>
    {:then}
      <Button on:click={authenticate} primary={true}>Connect Wallet</Button>
    {/await}
  {/if}
  <Provider data={dataContext}>
    <slot />
  </Provider>
</div>
