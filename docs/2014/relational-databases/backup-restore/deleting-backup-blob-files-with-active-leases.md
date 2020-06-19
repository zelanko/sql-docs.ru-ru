---
title: Удаление резервных файлов больших двоичных объектов с активной арендой | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8301c1f88eb8cf928066a3c12b14452ddbd98cda
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84958514"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a>Удаление резервных файлов больших двоичных объектов с активной арендой
  При резервном копировании или восстановлении из хранилища Azure SQL Server получает бесконечную аренду для блокировки монопольного доступа к большому двоичному объекту. После успешного завершения процесса резервного копирования или восстановления аренда аннулируется. Если резервное копирование или восстановление оканчивается неудачей, то в процессе резервного копирования предпринимается попытка очистить все недействительные большие двоичные объекты. Но если резервное копирование оканчивается неудачей из-за длительного или неустранимого сбоя связи с сетью, то, возможно, в процессе резервного копирования нельзя будет получить доступ к большому двоичному объекту и он останется потерянным. Это означает, что большой двоичный объект не может быть записан или удален до тех пор, пока аренда не освободится. В этом разделе показано, как освободить и удалить зарезервированный большой двоичный объект.  
  
 Дополнительные сведения о типах аренды см. в этой [статье](https://go.microsoft.com/fwlink/?LinkId=275664).  
  
 Если операция резервного копирования не удается, это может привести к появлению файла резервной копии, который является нерабочим.  Также у большого двоичного объекта файла может появиться активная аренда, которая предотвращает его удаление и повторную запись.  Чтобы удалить или повторно записать такие большие двоичные объекты, необходимо вначале прекратить аренду. Если происходят ошибки при резервном копировании, рекомендуется очистить аренды и удалить большие двоичные объекты. Также можно внести периодическую чистку в задачи управления хранилищем.  
  
 Если происходит ошибка восстановления, то последующие операции восстановления не блокируются, поэтому проблем с активной арендой не возникает. Прерывайте аренду только в том случае, если необходимо перезаписать или удалить большой двоичный объект.  
  
## <a name="managing-orphaned-blobs"></a>Управление потерянными большими двоичными объектами  
 Следующие действия описывают процесс очистки после неудачной операции резервного копирования или восстановления. Все действия могут быть выполнены с помощью скриптов PowerShell. Пример кода представлен в следующем разделе:  
  
1.  **Определение больших двоичных объектов с арендой.** Если резервное копирование выполняется с помощью скрипта или процесса, вы можете фиксировать ошибки внутри такого скрипта или процесса и использовать эти данные для очистки больших двоичных объектов.   Можно также использовать свойства LeaseStats и LeastState, чтобы выделить большие двоичные объекты с арендой. После определения больших двоичных объектов рекомендуется просмотреть список, проверить работоспособность файла резервной копии перед удалением большого двоичного объекта.  
  
2.  **Прерывание аренды.** Авторизованный запрос может прерывать аренду без предоставления идентификатора аренды. Дополнительные сведения см. в [этом разделе](https://go.microsoft.com/fwlink/?LinkID=275664) .  
  
    > [!TIP]  
    >  SQL Server выдает идентификатор аренды для получения монопольного доступа во время операции восстановления. Идентификатор аренды при операции восстановления — BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.  
  
3.  **Удаление большого двоичного объекта.** Чтобы удалить большой двоичный объект с активной арендой, сначала необходимо прервать аренду.  
  
###  <a name="powershell-script-example"></a><a name="Code_Example"></a>Пример сценария PowerShell  
 ** \* \* Важно \* ! \* ** если вы используете PowerShell 2,0, возможно, возникли проблемы при загрузке сборки Microsoft WindowsAzure.Storage.dll. Рекомендуется обновить Powershell до версии 3.0, чтобы решить проблему. Можно также использовать следующее решение для PowerShell 2.0:  
  
-   Создайте или измените файл powershell.exe.config для загрузки сборки .NET Framework 2.0 и .NET Framework 4.0 в среде выполнения с помощью следующего:  
  
    ```xml
    <?xml version="1.0"?>
    <configuration>
        <startup useLegacyV2RuntimeActivationPolicy="true">
            <supportedRuntime version="v4.0.30319"/>
            <supportedRuntime version="v2.0.50727"/>
        </startup>
    </configuration>
    ```  
  
 В следующем примере показано определение больших двоичных объектов с активной арендой и ее последующее прерывание. В этом примере также показано, как отфильтровывать идентификаторы аренды.  
  
 Советы для запуска этого скрипта  
  
> [!WARNING]  
>  Если резервное копирование в службу хранилища BLOB-объектов Azure выполняется одновременно с этим сценарием, то резервное копирование может завершиться ошибкой, так как этот скрипт прервет аренду, которую резервная копия пытается получить в то же время. Рекомендуется выполнять этот скрипт во время перерывов на профилактическое техобслуживание или в то время, когда не ожидается проведение какого-либо резервного копирования.  
  
1.  При выполнении этого скрипта вам будет предложено указать значения для учетной записи хранения, ключа хранилища, контейнера, пути к сборке службы хранилища Azure и параметров имени. Путь к сборке хранилища — это установочная директория экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имя файла для сборки хранилища — Microsoft.WindowsAzure.Storage.dll. Далее приводится пример запросов и введенных значений.  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  При отсутствии больших двоичных объектов с заблокированными арендами появится следующее сообщение:  
  
     **Отсутствуют большие двоичные объекты с заблокированным статусом аренды**  
  
     При наличии больших двоичных объектов с заблокированными арендами появится следующее сообщение:  
  
     **Прерывание аренды**  
  
     **Аренда — это \<URL of the Blob> Аренда восстановления. это сообщение появляется только в том случае, если у вас есть большой двоичный объект с арендой восстановления, которая еще активна.**  
  
     **Аренда в \<URL of the Blob> не является арендой восстановления, в которую включена аренда \<URL of the Bob> .**  
  
```powershell
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
{
    Write-Host " There are no blobs with locked lease status"  
}

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases"  
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}
```  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
