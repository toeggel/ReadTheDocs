# Github
## Action
__Example > Build and Deploy Gatsby page to gh-pages__
1. Generate a token on Github (select repo): https://github.com/settings/tokens
2. Copy token and insert as new Secret in the repository where you like to use it.
3. Create action  (se example)

```
on:
  push:
    branches:
      - main
name: Build and Deploy Gatsby
jobs:
  build_gatsby:
    name: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1

      - name: yarn install
        run: yarn install

      - name: gatsby build
        env:
          GH_API_KEY: ${{ secrets.YOUR_SECRET_NAME }}
        run: yarn build

      - name: deploy
        uses: maxheld83/ghpages@v0.2.1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GH_PAT: ${{ secrets.YOUR_SECRET_NAME }}
          BUILD_DIR: "public/"
```