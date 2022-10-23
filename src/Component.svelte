<script>
  import { getContext } from 'svelte'

  const { styleable, Provider } = getContext('sdk')
  const component = getContext('component')

  let web3Provider = undefined
  $: dataContext = {
    web3Provider
  }
</script>

<div use:styleable={$component.styles}>
  <Provider data={dataContext}>
    <slot />
  </Provider>
</div>
