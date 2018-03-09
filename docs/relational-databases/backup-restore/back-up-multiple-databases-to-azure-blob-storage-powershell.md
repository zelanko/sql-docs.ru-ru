---
title: "Резервное копирование нескольких баз данных в службу хранилища BLOB-объектов Azure с использованием PowerShell | Документация Майкрософт"
ms.custom: 
ms.date: 05/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
caps.latest.revision: "13"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28c5b537cfaf991b5067142e79d4857e002452e8
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="back-up-multiple-databases-to-azure-blob-storage---powershell"></a>Резервное копирование нескольких баз данных в службу хранилища BLOB-объектов Azure с использованием PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе приведены образцы скриптов, которые можно использовать для автоматизации резервного копирования в службу хранилища больших двоичных объектов Windows Azure с помощью командлетов PowerShell.  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a>Обзор командлетов PowerShell для резервного копирования и восстановления  
 **Backup-SqlDatabase** и **Restore-SqlDatabase** — два основных командлета для операций резервного копирования и восстановления. Помимо них имеются другие командлеты, которые могут потребоваться для автоматизации резервного копирования в хранилище больших двоичных объектов Windows Azure, такие как набор командлетов **SqlCredential** . Ниже приведен список командлетов PowerShell, доступных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и используемых в операциях резервного копирования и восстановления.  
  
 Backup-SqlDatabase  
 Этот командлет используется для создания резервной копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Restore-SqlDatabase  
 Используется для восстановления базы данных.  
  
 New-SqlCredential  
 Этот командлет используется для создания учетных данных SQL, которые будут использоваться для резервного копирования SQL Server в хранилище Windows Azure. Дополнительные сведения об учетных данных и их использовании в операциях резервного копирования и восстановления SQL Server см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища Blob-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 Get-SqlCredential  
 Этот командлет используется для получения объекта учетных данных и его свойств.  
  
 Remove-SqlCredential  
 Удаление объекта учетных данных SQL  
  
 Set-SqlCredential  
 Этот командлет используется для изменения или задания свойств объекта учетных данных SQL.  
  
> [!TIP]  
>  Командлеты учетных данных используются в операциях резервного копирования и восстановления в сценариях хранилищ больших двоичных объектов Windows Azure.  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a>PowerShell для операций резервного копирования для нескольких баз данных и нескольких экземпляров  
 Следующие разделы содержат скрипты для различных операций, таких как создание учетных данных SQL в нескольких экземплярах SQL Server, резервное копирование всех пользовательских баз данных в экземпляре SQL Server и т. д. С помощью этих скриптов можно автоматизировать или запланировать операции резервного копирования в соответствии с требованиями среды. Скрипты, описанные здесь, являются примерами, и их можно изменять или расширять для конкретной среды.  
  
 Ниже приведены замечания для примеров скриптов.  
  
1.  **Навигация по путям SQL Server PowerShell.** В Windows PowerShell предусмотрены командлеты для навигации по структуре пути, которая представляет иерархию объектов, поддерживаемых поставщиком PowerShell. После перехода к нужному узлу можно использовать другие командлеты для выполнения основных операций с текущим объектом.  
  
2.  Командлет**Get-ChildItem** . Сведения, возвращаемые командлетом **Get-ChildItem** , зависят от расположения в пути SQL Server PowerShell. Например, если размещение находится на уровне компьютера, командлет возвращает все экземпляры ядра СУБД SQL Server, установленные на компьютере. Другой пример: если расположение находится на уровне объектов, таких как базы данных, командлет возвращает список объектов базы данных.  По умолчанию командлет **Get-ChildItem** не возвращает системные объекты.  Системные объекты можно просмотреть, задав параметр –Force.  
  
     Дополнительные сведения см. в статье [Navigate SQL Server PowerShell Paths](../../relational-databases/scripting/navigate-sql-server-powershell-paths.md).  
  
3.  Несмотря на то что каждый образец кода можно использовать отдельно, изменив значения переменных, создание учетной записи хранения Windows Azure и учетных данных SQL является предварительным условием и необходимо для всех операций резервного копирования и восстановления в службе хранилища больших двоичных объектов Windows Azure.  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a>Создание учетных данных SQL для всех экземпляров SQL Server  
 Имеется два образца скрипта, и оба создают учетные данные SQL «mybackupToURL» на всех экземплярах SQL Server на компьютере. В первом простом примере создаются учетные данные и не перехватываются исключения.  Например, если в одном из экземпляров на компьютере уже существуют учетные данные с тем же именем, работа скрипта завершится сбоем. Второй пример перехватывает ошибки, что позволяет продолжить выполнение скрипта.  
  
```  
  
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = convertto-securestring $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd SQLServer:\SQL\$env:COMPUTERNAME  
# get the list of instances  
$instances = Get-childitem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | new-sqlcredential -Name $credentialName  -Identity $storageAccount -Secret $secureString  
```  
  
```  
  
import-module sqlps  
  
# set the parameter values  
  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = convertto-securestring $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd SQLServer:\SQL\$env:COMPUTERNAME  
# get the list of instances  
$instances = Get-childitem  
#loop through instances and create a SQL credential, output any errors  
foreach ($instance in $instances)  
{  
    Try  
{  
     new-sqlcredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop   
}  
Catch [Exception]  
    {  
  
            write-host "instance - $($instance.name): "$_.Exception.Message  
  
    }  
  
 }  
  
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a>Удаление учетных данных SQL для всех экземпляров SQL Server  
 Этот скрипт может использоваться для удаления конкретных учетных данных из всех экземпляров SQL Server, установленных на компьютере. Если объект учетных данных не существует в определенном экземпляре, выводится сообщение об ошибке, а скрипт продолжает выполняться до тех пор, пока не будут проверены все экземпляры.  
  
```  
  
import-module sqlps  
  
cd SQLServer:\SQL\$env:COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-childitem  
  
foreach ($instance in $instances)  
   {   
    try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-sqlCredential -path $path -ea stop   
         }  
         catch [Exception]  
         {  
            write-host $_.Exception.Message  
  
        }  
  
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a>Полное резервное копирование для всех баз данных (ВКЛЮЧАЯ СИСТЕМНЫЕ)  
 Следующий скрипт создает резервные копии всех баз данных на компьютере. Это касается и пользовательских баз данных, и системной базы данных **msdb** . Скрипт фильтрует системные базы данных **tempdb** и **model** .  
  
```  
  
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level  
  
cd SQLServer:\SQL\$env:COMPUTERNAME  
$instances = Get-childitem   
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 foreach ($instance in $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = get-childitem -Force -path $path |Where-object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
  
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }  
  
```  
  
### <a name="full-database-backup-for-all-user-databases"></a>Полное резервное копирование для ВСЕХ пользовательских баз данных  
 Следующий скрипт можно использовать для резервного копирования всех пользовательских баз данных во всех экземплярах SQL Server на компьютере.  
  
```  
  
import-module sqlps   
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level  
  
cd SQLServer:\SQL\$env:COMPUTERNAME  
$instances = Get-childitem   
# loop through each instances and backup up all the user databases  
 foreach ($instance in $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
   $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On   
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a>Полное резервное копирование баз данных MASTER и MSDB (СИСТЕМНЫХ БАЗ ДАННЫХ) для всех экземпляров SQL Server  
 Следующий скрипт можно использовать для резервного копирования баз данных **master** и **msdb** во всех экземплярах SQL Server, установленных на компьютере.  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd SQLServer:\SQL\$env:COMPUTERNAME  
$instances = Get-childitem   
foreach ($instance in $instances)  
 {  
      foreach ($s in $sysdbs)  
     {  
Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}    
 }  
  
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a>Полное резервное копирование всех пользовательских баз данных для одного экземпляра SQL Server  
 Следующий скрипт используется для резервного копирования только пользовательских баз данных, доступных на именованном экземпляре SQL Server. Тот же скрипт можно использовать для экземпляра по умолчанию на компьютере, изменив значение параметра $srvPath.  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\$env:COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLServer:\SQL\$env:COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd SQLServer:\SQL\$env:COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a>Полное резервное копирование только системных баз данных (MASTER И MSDB) для одного экземпляра SQL Server  
 Полный скрипт можно использовать для резервного копирования баз данных **master** и **msdb** на именованном экземпляре SQL Server. Тот же скрипт можно использовать для экземпляра по умолчанию на компьютере, изменив значение параметра $srvPath.  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\$env:COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLServer:\SQL\$env:COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
foreach ($s in $sysDbs)   
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление SQL Server с помощью службы хранилища Blob-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
