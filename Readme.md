My Project is visible on this url
https://ostad-assignment.pranto.dev/

1.  Create a folder on my server for project
2.  Create a FTP account for access my sercer folder path
3.  Add FTP credentials on Github Repository -> Setting -> Secrets and variables -> Actions
4.  Added 3 secret on there
5.  Then create an action workflow on github action for main branch name set main.yml and added this code
    name: Publish Website to CPanel
    on:
    push:
    branches: - main
    jobs:
    FTP-Deploy-Action:
    name: FTP-Deploy-Action
    runs-on: ubuntu-latest
    steps: - uses: actions/checkout@v2.1.0
    with:
    fetch-depth: 2 - name: FTP-Deploy-Action
    uses: SamKirkland/FTP-Deploy-Action@4.3.3
    with:
    server: ${{ secrets.FTP_SERVER }}
    username: ${{ secrets.FTP_USERNAME }}
    password: ${{ secrets.FTP_PASSWORD }}
