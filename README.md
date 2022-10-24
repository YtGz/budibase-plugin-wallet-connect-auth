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
