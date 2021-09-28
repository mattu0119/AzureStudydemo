# AzureStudydemo

+ [AppService Team blog](https://azure.github.io/AppService/)
+ [Azure App Service Zero to Hero by Sigma](https://www.sigmact.com/updated/zero-to-hero/)
+ [デプロイのベストプラクティス](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-best-practices#continuously-deploy-code)
+ [クイックスタート: ASP.NET Web アプリをデプロイする](https://docs.microsoft.com/ja-jp/azure/app-service/quickstart-dotnetcore?tabs=netcore31&pivots=development-environment-vscode)
+ [Azure DevOps Demo Generator](https://azuredevopsdemogenerator.azurewebsites.net/)
+ [GIthub Public IP addresses](https://docs.github.com/en/rest/reference/meta)
+ [負荷テストツール](https://app.k6.io/)

* App Service のネットワークACL は最大512個までしか登録できない。
```Powershell
$priority = 200;
$json = Invoke-RestMethod -Uri "https://api.github.com/meta"
foreach($ip in $json.actions){
    if($ip -like "*.*"){
        az webapp config access-restriction add -g AzureStudyDemo -n azurestudydemo --slot dev --rule-name $ip --action Allow --ip-address $ip --priority $priority
        Write-Output "$($ip) added to rules."
        $priority++
    }
}
```

* Github Actions で利用する IP Address の確認
```Powershell
$json = Invoke-RestMethod -Uri "https://api.github.com/meta"
$json.actions | Where-Object {$_ -Like "*.*"} > .\actions.txt
```
+ [Install Powershell 7.1](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7.1)
+ [Install Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli)
+ [How to whitelist with Github Actions in Azure Webapp using Github's API](https://stackoverflow.com/questions/68011051/how-do-i-whitelist-github-actions-ip-addresses-in-azure-web-app-using-githubs-a)


## git 
```Powershell
git add .
git commit -m "comment"
git push origin main
```