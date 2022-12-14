# Gitopia Mirror Action

GitHub action to mirror your GitHub repos on Gitopia

Use it as the following gitopia-mirror.yml

```
name: Mirror to Gitopia

on:
  push:
    branches:
      - '**'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
        with:
          fetch-depth: 0
      - name: Push to Gitopia mirror
        uses: gitopia/gitopia-mirror-action@v0.5.0
        with:
          gitopiaWallet: "${{ secrets.GITOPIA_WALLET }}"
          remoteUrl: "gitopia://gitopia10j4ryjjna69hvsrahgvhwjv3dd46tt6xuprguq/gitopia-mirror-action"

```

Add Gitopia wallet contents to GitHub secrets called `GITOPIA_WALLET`

## Input details

- `gitopiaWallet`: Your wallet file saved as a GitHub secret,
- `remoteUrl`: Your Gitopia repository remote_url created from https://gitopia.com
- `force` (optional): true/false, Force push to gitopia remote repository? Default is false, setting this to true will allow the mirror action to overwrite your gitopia remote repository. The changes done directly in your gitopia remote repository will be overwritten.
