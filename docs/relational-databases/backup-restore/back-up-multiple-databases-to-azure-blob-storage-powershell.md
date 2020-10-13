---
title: 'Резервное копирование нескольких баз данных: хранилище BLOB-объектов Azure'
description: В этой статье приведены примеры скриптов, которые можно использовать для автоматизации резервного копирования в SQL Server в службу хранилища BLOB-объектов Azure с помощью командлетов PowerShell.
titleSuffix: PowerShell
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e79840f828a7891ac3e01cd52721eb5755a97c7b
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809254"
---
# <a name="back-up-multiple-databases-to-azure-blob-storage---powershell"></a>Резервное копирование нескольких баз данных в службу хранилища BLOB-объектов Azure с использованием PowerShell

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом разделе приведены примеры скриптов, которые можно использовать для автоматизации резервного копирования в службу хранилища BLOB-объектов Azure с помощью командлетов PowerShell.  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a>Обзор командлетов PowerShell для резервного копирования и восстановления

**Backup-SqlDatabase** и **Restore-SqlDatabase** — два основных командлета для операций резервного копирования и восстановления.

Помимо них, имеются другие командлеты, которые могут потребоваться для автоматизации резервного копирования в хранилище BLOB-объектов Microsoft Azure, такие как набор командлетов **SqlCredential**.

Список всех доступных командлетов см. в разделе [Командлеты SqlServer](/powershell/module/sqlserver).
  
> [!TIP]  
> Командлеты **SqlCredential** используются в операциях резервного копирования и восстановления в сценариях работы с хранилищем BLOB-объектов Azure. Дополнительные сведения об учетных данных и их использовании см. в статье [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a>PowerShell для операций резервного копирования для нескольких баз данных и нескольких экземпляров

Следующие разделы содержат скрипты для различных операций, таких как создание учетных данных SQL в нескольких экземплярах SQL Server, резервное копирование всех пользовательских баз данных в экземпляре SQL Server и т. д. С помощью этих скриптов можно автоматизировать или запланировать операции резервного копирования в соответствии с требованиями среды. Скрипты, описанные здесь, являются примерами, и их можно изменять или расширять для конкретной среды.  
  
Ниже приведены замечания для примеров скриптов.  
  
- В SQL Server PowerShell предусмотрены командлеты для навигации по структуре пути, которая представляет иерархию объектов, поддерживаемых поставщиком PowerShell. После перехода к нужному узлу можно использовать другие командлеты для выполнения основных операций с текущим объектом.

  Дополнительные сведения см. в статье [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md).

- Командлет **Get-ChildItem**. Сведения, возвращаемые **Get-ChildItem**, зависят от расположения в пути SQL Server PowerShell. Например, если размещение находится на уровне компьютера, командлет возвращает все экземпляры ядра СУБД SQL Server, установленные на компьютере. Либо если расположение находится на уровне объектов, таких как базы данных, командлет возвращает список объектов базы данных. По умолчанию командлет **Get-ChildItem** не возвращает системные объекты. Для просмотра системных объектов используйте параметр `–Force`.

- Учетная запись хранения Azure и учетные данные SQL требуются для всех операций резервного копирования и восстановления в службе хранилища BLOB-объектов Azure.
  
### <a name="create-a-sql-credential-on-all-instances-of-sql-server"></a>Создание учетных данных SQL для всех экземпляров SQL Server

Приведенный ниже скрипт можно использовать для создания общих учетных данных SQL во всех экземплярах SQL Server на компьютере. Если в одном из экземпляров на компьютере уже есть учетные данные с тем же именем, скрипт выводит ошибку и продолжает выполнение.  
  
```powershell
# load the sqlps module
import-module sqlps  
  
# set parameters
$sqlPath = "sqlserver:\sql\$($env:COMPUTERNAME)"
$storageAccount = "<myStorageAccount>"  
$storageKey = "<myStorageAccessKey>"  
$secureString = ConvertTo-SecureString $storageKey -AsPlainText -Force  
$credentialName = "myCredential-$(Get-Random)"

Write-Host "Generate credential: " $credentialName
  
#cd to sql server and get instances  
cd $sqlPath
$instances = Get-ChildItem

#loop through instances and create a SQL credential, output any errors
foreach ($instance in $instances)  {
    try {
        $path = "$($sqlPath)\$($instance.DisplayName)\credentials"
        New-SqlCredential -Name $credentialName -Identity $storageAccount -Secret $secureString -Path $path -ea Stop | Out-Null
        Write-Host "...generated credential $($path)\$($credentialName)."  }
    catch { Write-Host $_.Exception.Message } }
```

> [!NOTE]
> Оператор `-ea Stop | Out-Null` используется для вывода пользовательского исключения. Если вы предпочитаете сообщения об ошибках, используемые в PowerShell по умолчанию, этот оператор можно удалить. 

### <a name="remove-a-sql-credential-from-all-instances-of-sql-server"></a>Удаление учетных данных SQL из всех экземпляров SQL Server

Приведенный ниже скрипт можно использовать для удаления конкретных учетных данных из всех экземпляров SQL Server, установленных на компьютере. Если учетные данные не существуют в определенном экземпляре, выводится сообщение об ошибке, а скрипт продолжает выполняться до тех пор, пока не будут проверены все экземпляры.  
  
```powershell
import-module sqlps

$sqlPath = "sqlserver:\sql\$($env:COMPUTERNAME)"
$credentialName = "<myCredential>"

Write-Host "Delete credential: " $credentialName

cd $sqlPath
$instances = Get-ChildItem

#loop through instances and delete a SQL credential
foreach ($instance in $instances)  {
    try {
        $path = "$($sqlPath)\$($instance.DisplayName)\credentials\$($credentialName)"
        Remove-SqlCredential -Path $path -ea Stop | Out-Null
        Write-Host "...deleted credential $($path)."  }
    catch { Write-Host $_.Exception.Message } }
```  
  
### <a name="full-backup-for-all-databases"></a>Полное резервное копирование всех баз данных

Следующий скрипт создает резервные копии всех баз данных на компьютере. Это касается и пользовательских баз данных, и системной базы данных **msdb** . Скрипт фильтрует системные базы данных **tempdb** и **model** .  
  
```powershell
import-module sqlps  

$sqlPath = "sqlserver:\sql\$($env:COMPUTERNAME)"
$storageAccount = "<myStorageAccount>"  
$blobContainer = "<myBlobContainer>"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "<myCredential>"

Write-Host "Backup database: " $backupUrlContainer
  
cd $sqlPath
$instances = Get-ChildItem

#loop through instances and backup all databases (excluding tempdb and model)
foreach ($instance in $instances)  {
    $path = "$($sqlPath)\$($instance.DisplayName)\databases"
    $databases = Get-ChildItem -Force -Path $path | Where-object {$_.name -ne "tempdb" -and $_.name -ne "model"}

    foreach ($database in $databases) {
        try {
            $databasePath = "$($path)\$($database.Name)"
            Write-Host "...starting backup: " $databasePath
            Backup-SqlDatabase -Database $database.Name -Path $path -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On
            Write-Host "...backup complete."  }
        catch { Write-Host $_.Exception.Message } } }
```  
  
### <a name="full-backup-for-system-databases-only-on-a-specific-instance-of-sql-server"></a>Полное резервное копирование системных баз данных для определенного экземпляра SQL Server

Полный скрипт можно использовать для резервного копирования баз данных **master** и **msdb** на именованном экземпляре SQL Server. Тот же скрипт можно использовать для любого экземпляра, изменив значение параметра instance. Экземпляр SQL Server по умолчанию называется `DEFAULT`.
  
```powershell
import-module sqlps  

$sqlPath = "sqlserver:\sql\$($env:COMPUTERNAME)"
$instanceName = "DEFAULT"
$storageAccount = "<myStorageAccount>"  
$blobContainer = "<myBlobContainer>"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "<myCredential>"

Write-Host "Backup database: " $instanceName " to " $backupUrlContainer
  
cd "$($sqlPath)\$($instanceName)"

#loop through instance and backup specific databases
$databases = "master", "msdb"  
foreach ($database in $databases) {
    try {
        Write-Host "...starting backup: " $database
        Backup-SqlDatabase -Database $database -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On
        Write-Host "...backup complete." }
    catch { Write-Host $_.Exception.Message } }
```  
  
## <a name="see-also"></a>См. также раздел

[Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)

[Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md).