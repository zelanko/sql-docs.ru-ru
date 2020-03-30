---
title: Удаление резервных файлов больших двоичных объектов с активной арендой | Документация Майкрософт
ms.custom: ''
ms.date: 08/17/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdc58884e65fb243bbb75f257e19ccef3faa2b9f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72908933"
---
# <a name="delete-backup-blob-files-with-active-leases"></a>Удаление резервных файлов больших двоичных объектов с активной арендой

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

При создании резервной копии или восстановлении с помощью хранилища Microsoft Azure SQL Server получает бесконечную аренду для блокировки монопольного доступа к большому двоичному объекту. После успешного завершения процесса резервного копирования или восстановления аренда аннулируется. Если резервное копирование или восстановление оканчивается неудачей, то в процессе резервного копирования предпринимается попытка очистить все недействительные большие двоичные объекты. Но если резервное копирование оканчивается неудачей из-за длительного или неустранимого сбоя связи с сетью, то, возможно, в процессе резервного копирования нельзя будет получить доступ к большому двоичному объекту и он останется потерянным. Это означает, что большой двоичный объект не может быть записан или удален до тех пор, пока аренда не освободится. В этом разделе показано, как освободить (прервать) аренду и удалить большой двоичный объект.
  
Дополнительные сведения о типах аренды см. в этой [статье](https://go.microsoft.com/fwlink/?LinkId=275664).  
  
Если операция резервного копирования завершается ошибкой, это может привести к появлению недопустимого файла резервной копии. Также у большого двоичного объекта файла может появиться активная аренда, которая предотвращает его удаление и повторную запись. Чтобы удалить или повторно записать такие большие двоичные объекты, необходимо вначале прекратить аренду. Если при резервном копировании происходят ошибки, рекомендуется очистить аренды и удалить большие двоичные объекты. Также можно внести периодическую чистку в задачи управления хранилищем.  
  
Если происходит ошибка восстановления, то последующие операции восстановления не блокируются, поэтому проблем с активной арендой не возникает. Прерывайте аренду только в том случае, если необходимо перезаписать или удалить большой двоичный объект.  
  
## <a name="manage-orphaned-blobs"></a>Управление потерянными большими двоичными объектами

Следующие действия описывают процесс очистки после неудачной операции резервного копирования или восстановления. Все действия могут быть выполнены с помощью скриптов PowerShell. В следующем разделе приводится пример скрипта PowerShell.  
  
1. **Определение больших двоичных объектов с арендой.** Если резервное копирование выполняется с помощью скрипта или процесса, вы можете фиксировать ошибки внутри такого скрипта или процесса и использовать эти данные для очистки больших двоичных объектов.  Можно также использовать свойства LeaseStats и LeastState, чтобы определить большие двоичные объекты с арендой. После определения больших двоичных объектов просмотрите список и проверьте работоспособность файла резервной копии перед удалением большого двоичного объекта.  
  
1. **Прерывание аренды.** Авторизованный запрос может прерывать аренду без предоставления идентификатора аренды. Дополнительные сведения см. в [этом разделе](https://go.microsoft.com/fwlink/?LinkID=275664) .  
  
    > [!TIP]  
    > SQL Server выдает идентификатор аренды для получения монопольного доступа во время операции восстановления. Идентификатор аренды при операции восстановления — BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.  
  
1. **Удаление большого двоичного объекта.** Чтобы удалить большой двоичный объект с активной арендой, сначала необходимо прервать аренду.  

###  <a name="powershell-script-example"></a><a name="Code_Example"></a> Пример скрипта PowerShell  
  
> [!IMPORTANT]
> Если запущена оболочка PowerShell 2.0, то могут возникнуть проблемы при загрузке сборки Microsoft WindowsAzure.Storage.dll. Чтобы решить эту проблему, рекомендуется обновить [PowerShell](https://docs.microsoft.com/powershell/). Вы также можете использовать следующее обходное решение, чтобы создать или изменить файл powershell.exe.config для загрузки сборок .NET 2.0 и .NET 4.0 во время выполнения:  
>
> ```xml
> <?xml version="1.0"?>
>     <configuration>
>         <startup useLegacyV2RuntimeActivationPolicy="true">
>             <supportedRuntime version="v4.0.30319"/>
>             <supportedRuntime version="v2.0.50727"/>
>         </startup>
>     </configuration>  
> ```  
  
 В следующем примере скрипта показано определение больших двоичных объектов с активной арендой и ее последующее прерывание. В этом примере также показано, как отфильтровывать идентификаторы аренды.  
  
#### <a name="tips-on-running-this-script"></a>Советы для запуска этого скрипта
  
> [!WARNING]  
> Если операция резервного копирования в службе хранилища BLOB-объектов Azure выполняется одновременно с этим скриптом, то резервное копирование может окончиться неудачей, так как скрипт прервет аренду, которую операция резервного копирования пытается осуществить в то же время. Выполняйте этот скрипт во время перерывов на профилактическое техобслуживание или в то время, когда не ожидается проведение резервного копирования.  
  
- Перед запуском этого скрипта следует добавить значения для параметров учетной записи хранения, ключа хранилища, контейнера, пути к сборке хранилища Azure и ее имени. Путь к сборке хранилища — это установочная директория экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имя файла для сборки хранилища — Microsoft.WindowsAzure.Storage.dll.
  
- При отсутствии больших двоичных объектов с заблокированными арендами появится следующее сообщение: `There are no blobs with locked lease status`
  
- При наличии больших двоичных объектов с заблокированными арендами появятся следующие сообщения: `Breaking Leases`, `The lease on <URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.` и `The lease on <URL of the Blob> is not a restore lease Breaking lease on <URL of the Bob>.`
  
```powershell
$storageAccount = "<myStorageAccount>"
$storageKey = "<myStorageKey>"
$blobContainer = "<myBlobContainer>"
$storageAssemblyPathName = "<myStorageAssemblyPathName>"
  
# well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
# list all the blobs  
$blobs = $container.ListBlobs($null,$true)
  
# filter blobs that are have Lease Status as "locked"
$lockedBlobs = @()  
foreach($blob in $blobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases..."
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease."  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease."  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)."  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
} else { Write-Host " There are no blobs with locked lease status." }
```  
  
## <a name="see-also"></a>См. также раздел

[Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
