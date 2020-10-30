# gitopia-mirror-action

Github action to mirror your Github repos to Gitopia

Use it as the following mirror.yml

```
name: Mirror to Gitopia

on:
  push:
    branches: [master]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: 12
          registry-url: https://registry.npmjs.org/
      - name: Test action
        uses: gitopia/gitopia-mirror-action@master
        # The action should not publish any real changes, but should succeed.
        with:
          gitopiaWallet: "${{ secrets.GITOPIA_WALLET }}"
          branch: "master"
          remoteUrl: "gitopia://jf9rQRuE_TnKi5stRHbGk8pjtVKQ_0ikFs8tfYyZLMs/gitopia-mirror-action"

```

Add Arweave Wallet contents to a wallet and add it in secrets

Update values of
`gitopiaWallet` - your wallet file pointing to the secret containg your wallet,
`branch` - the branch to Gitopia your want to push (optional),
`remoteUrl` - your repository remote url created from https://gitopia.org
