---
title: "Занятие 1. Создание хранимой политики доступа и подписанного URL-адреса | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2c8af4701b9a01ee21613fe7e093a89f1d8f990
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-1-create-stored-access-policy-and-shared-access-signature"></a>Занятие 1. Создание хранимой политики доступа и подписанного URL-адреса
На этом занятии вы используете скрипт [Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) , чтобы создать подписанный URL-адрес для контейнера BLOB-объектов Azure с помощью хранимой политики доступа.  
  
> [!NOTE]  
> Этот скрипт написан с помощью Azure PowerShell 5.0.10586.  
  
Подписанный URL-адрес — это универсальный код ресурса (URI), который предоставляет ограниченные права доступа к контейнерам, большим двоичным объектам, очередям и таблицам. Хранимая политика доступа предоставляет дополнительный уровень контроля над сервером, включая отзыв, истечение срока действия и продление доступа. При использовании этого расширения необходимо создать политику в контейнере как минимум с правами на чтение, запись и перечисление.  
  
Хранимую политику доступа и подписанный URL-адрес можно создать с помощью Azure PowerShell, пакет Azure Storage SDK, Azure REST API или служебной программы стороннего производителя. В этом учебнике демонстрируется применение скрипта Azure PowerShell для выполнения данной задачи. В скрипте используется модель развертывания диспетчера ресурсов и создаются следующие ресурсы:  
  
-   Группа ресурсов  
  
-   Учетная запись хранения  
  
-   Контейнер BLOB-объектов Azure  
  
-   Политика SAS  
  
Выполнение скрипта начинается с объявления ряда переменных для указания имен перечисленных выше ресурсов и имен следующих обязательных входных значений:  
  
-   имя префикса, используемое для именования других объектов ресурсов;  
  
-   имя подписки;  
  
-   расположение центра обработки данных.  
  
> [!NOTE]  
> Этот скрипт написан так, что позволяет вам использовать либо ARM, либо классические ресурсы модели развертывания.  
  
В результате выполнения скрипта создается соответствующая инструкция CREATE CREDENTIAL, которая будет использоваться на [занятии 2 "Создание учетных данных SQL Server с помощью подписанного URL-адреса"](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md). Эта инструкция копируется в буфер обмена и выводится в консоль.  
  
Чтобы создать политику для контейнера и ключ подписанного URL-адреса, выполните указанные ниже действия.  
  
1.  Откройте интегрированную среду сценариев Window PowerShell или Windows PowerShell (см. требования к версии выше).  
  
2.  Измените, а затем выполните приведенный ниже скрипт.  
  
    ```  
    \<#   
    This script uses the Azure Resource model and creates a new ARM storage account.  
    Modify this script to use an existing ARM or classic storage account   
    using the instructions in comments within this script  
    #>  
    # Define global variables for the script  
    $prefixName = '<a prefix name>'  # used as the prefix for the name for various objects  
    $subscriptionName='<your subscription name>'   # the name  of subscription name you will use  
    $locationName = '<a data center location>'  # the data center region you will use  
    $storageAccountName= $prefixName + 'storage' # the storage account name you will create or use  
    $containerName= $prefixName + 'container'  # the storage container name to which you will attach the SAS policy with its SAS token  
    $policyName = $prefixName + 'policy' # the name of the SAS policy  
  
    \<#   
    Using Azure Resource Manager deployment model  
    Comment out this entire section and use the classic storage account name to use an existing classic storage account  
    #>  
  
    # Set a variable for the name of the resource group you will create or use  
    $resourceGroupName=$prefixName + 'rg'   
  
    # adds an authenticated Azure account for use in the session   
    Login-AzureRmAccount    
  
    # set the tenant, subscription and environment for use in the rest of   
    Set-AzureRmContext -SubscriptionName $subscriptionName   
  
    # create a new resource group - comment out this line to use an existing resource group  
    New-AzureRmResourceGroup -Name $resourceGroupName -Location $locationName   
  
    # Create a new ARM storage account - comment out this line to use an existing ARM storage account  
    New-AzureRmStorageAccount -Name $storageAccountName -ResourceGroupName $resourceGroupName -Type Standard_RAGRS -Location $locationName   
  
    # Get the access keys for the ARM storage account  
    $accountKeys = Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $storageAccountName  
  
    # Create a new storage account context using an ARM storage account  
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys[0].Value 
  
    \<#  
    Using the Classic deployment model  
    Use the following four lines to use an existing classic storage account  
    #>  
    #Classic storage account name  
    #Add-AzureAccount  
    #Select-AzureSubscription -SubscriptionName $subscriptionName #provide an existing classic storage account  
    #$accountKeys = Get-AzureStorageKey -StorageAccountName $storageAccountName  
    #$storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys.Primary  
  
    # The remainder of this script works with either the ARM or classic sections of code above  
  
    # Creates a new container in blob storage  
    $container = New-AzureStorageContainer -Context $storageContext -Name $containerName  
    $cbc = $container.CloudBlobContainer  
  
    # Sets up a Stored Access Policy and a Shared Access Signature for the new container  
    $permissions = $cbc.GetPermissions();  
    $policyName = $policyName  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $policy.SharedAccessStartTime = $(Get-Date).ToUniversalTime().AddMinutes(-5)  
    $policy.SharedAccessExpiryTime = $(Get-Date).ToUniversalTime().AddYears(10)  
    $policy.Permissions = "Read,Write,List,Delete"  
    $permissions.SharedAccessPolicies.Add($policyName, $policy)  
    $cbc.SetPermissions($permissions);  
  
    # Gets the Shared Access Signature for the policy  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $sas = $cbc.GetSharedAccessSignature($policy, $policyName)  
    Write-Host 'Shared Access Signature= '$($sas.Substring(1))''  
  
    # Outputs the Transact SQL to the clipboard and to the screen to create the credential using the Shared Access Signature  
    Write-Host 'Credential T-SQL'  
    $tSql = "CREATE CREDENTIAL [{0}] WITH IDENTITY='Shared Access Signature', SECRET='{1}'" -f $cbc.Uri,$sas.Substring(1)   
    $tSql | clip  
    Write-Host $tSql  
  
    ```  
  
3.  По завершении выполнения скрипта инструкция CREATE CREDENTIAL будет находиться в буфере обмена для использования на следующем занятии.  
  
**Следующее занятие:**  
  
[Занятие 2. Создание учетных данных SQL Server с помощью подписанного URL-адреса](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="see-also"></a>См. также:  
[Использование подписанных URL-адресов (SAS)](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
[Create Container](https://msdn.microsoft.com/library/azure/dd179468.aspx)  
[Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx)  
[Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx)  
  
  
  


