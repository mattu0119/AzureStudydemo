# AzureStudydemo

+ [Azure App Service Zero to Hero](https://www.sigmact.com/updated/zero-to-hero/)
+ [デプロイのベストプラクティス](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-best-practices#continuously-deploy-code)
+ [クイックスタート: ASP.NET Web アプリをデプロイする](https://docs.microsoft.com/ja-jp/azure/app-service/quickstart-dotnetcore?tabs=netcore31&pivots=development-environment-vscode)
+ [Azure DevOps Demo Generator](https://azuredevopsdemogenerator.azurewebsites.net/)
+ [GIthub Public IP addresses](https://docs.github.com/en/rest/reference/meta)


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