---
title: "Развертывание проекта служб SSIS с помощью PowerShell | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: 37fe358eb7e11cb878ebd9b0c8356ac2295ca7e9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-with-powershell"></a>Развертывание проекта служб SSIS с помощью PowerShell
Этого краткого руководства показано, как использовать сценарий PowerShell для подключения к серверу базы данных и развернуть проект служб SSIS в каталоге служб SSIS.

## <a name="powershell-script"></a>Сценарий PowerShell
Предоставьте соответствующие значения для переменных в верхней части следующий сценарий, а затем выполните скрипт, чтобы развернуть проект служб SSIS.

> [!NOTE]
> Следующий пример использует проверку подлинности Windows. Чтобы использовать проверку подлинности SQL Server, замените `Integrated Security=SSPI;` аргумент с `User ID=<user name>;Password=<password>;`.

```powershell
# Variables
$SSISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"
$TargetServerName = "localhost"
$TargetFolderName = "Project1Folder"
$ProjectFilePath = "C:\Projects\Integration Services Project1\Integration Services Project1\bin\Development\Integration Services Project1.ispac"
$ProjectName = "Integration Services Project1"

# Load the IntegrationServices assembly
$loadStatus = [System.Reflection.Assembly]::Load("Microsoft.SQLServer.Management.IntegrationServices, "+
    "Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91, processorArchitecture=MSIL")

# Create a connection to the server
$sqlConnectionString = `
    "Data Source=" + $TargetServerName + ";Initial Catalog=master;Integrated Security=SSPI;"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $SSISNamespace".IntegrationServices" $sqlConnection

# Get the Integration Services catalog
$catalog = $integrationServices.Catalogs["SSISDB"]

# Create the target folder
$folder = New-Object $SSISNamespace".CatalogFolder" ($catalog, $TargetFolderName,
    "Folder description")
$folder.Create()

Write-Host "Deploying " $ProjectName " project ..."

# Read the project file and deploy it
[byte[]] $projectFile = [System.IO.File]::ReadAllBytes($ProjectFilePath)
$folder.DeployProject($ProjectName, $projectFile)

Write-Host "Done."
```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие возможности для развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Развертывание пакета служб SSIS из командной строки](./ssis-quickstart-deploy-cmdline.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполнения развернутого пакета. Чтобы запустить пакет, можно выбрать несколько средств и языков. Дополнительные сведения см. в следующих статьях:
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

