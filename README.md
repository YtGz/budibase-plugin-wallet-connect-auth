# Wallet Connect Auth

Integrates the
[Wallet Connect Auth SDK](https://docs.walletconnect.com/2.0/introduction/auth)
into Budibase.

# Description

Decentralized and passwordless onboarding flows for apps built with the
[Budibase](https://github.com/Budibase/budibase) low code platform.

## Instructions

To build your new plugin run the following command:

```
pnpm build
```

You can also re-build everytime you make a change to your plugin with the
command:

```
pnpm watch
```

_Note: If using `npm` or `yarn`, note the patch file
`patches/hash.js@1.1.7.patch`_

## Example

_Note: most wallets do not support v2 of the WalletConnect protocol yet. For
testing purposes https://react-auth-wallet.walletconnect.com can be used._

An example that demonstrates how this plugin can be used to hide some portion of
a page behind a web3 login can be found
[here](http://budibase-plugin-wallet-connect-auth.wirtenberger.dev/app/wallet-connect-auth).


### How to Use

1. Navigate to https://react-auth-wallet.walletconnect.com and copy the wallet address.

![grafik](https://user-images.githubusercontent.com/10178241/197637863-f1791f27-f47e-4d01-95f2-dc0aa4013c1b.png)

2. Navigate to http://budibase-plugin-wallet-connect-auth.wirtenberger.dev/app/wallet-connect-auth#/home/<address\>. Substitute `<address>` with the wallet address from the previous step.
  
3. Click on `Connect Wallet` to log in using a WalletConnect v2 compatible wallet.

![grafik](https://user-images.githubusercontent.com/10178241/197638520-043681f9-4475-4ae1-90c4-d43a62dcb523.png)

4. A QR code appears. You can also copy the URI by clicking the button at the bottom.

![grafik](https://user-images.githubusercontent.com/10178241/197639328-0e4d0e84-4443-4092-b377-ed33fbcc6418.png)

5. Navigate to https://react-auth-wallet.walletconnect.com and scan the QR code (or paste the URI).

![grafik](https://user-images.githubusercontent.com/10178241/197639428-e3453232-536d-4c8b-b983-300f5fbbb268.png)

7. Sign the authentication request.

![grafik](https://user-images.githubusercontent.com/10178241/197639572-4c322585-15dc-4189-b836-3bde115984d4.png)

8. After signing the request, the secret will be revealed at last.

![grafik](https://user-images.githubusercontent.com/10178241/197640615-65b30956-0b66-43e4-b8fa-ae57d93b53a6.png)

9. If the address supplied as a URL parameter differs from the address of the wallet you used to sign the authentication request, the secret will not be revealed. Try it out! 

![grafik](https://user-images.githubusercontent.com/10178241/197639698-1c08f65d-fa03-4f3d-bfa6-cc150f513995.png)

### Final Notes

The steps above demonstrate how the UX of a web3-based login flow could look like. The plugin provides the wallet address as context for child components. The plugin enables a vast array of use cases. Let me know what you come up with!
