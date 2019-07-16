---
title: managed_backup.sp_backup_config_basic (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_basic_TSQL
- sp_backup_config_basic
- managed_backup.sp_backup_config_basic
- managed_backup.sp_backup_config_basic_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_basic
- sp_backup_config_basic
ms.assetid: 3ad73051-ae9a-4e41-a889-166146e5508f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d09fa38377910c2960b43eb6534dba4546538b4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942120"
---
# <a name="managedbackupspbackupconfigbasic-transact-sql"></a>managed_backup.sp_backup_config_basic (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Настраивает [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] основные параметры для конкретной базы данных или экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Эта процедура может вызываться для для создания базовой управляемого резервного копирования конфигурации. Тем не менее, если вы планируете добавить возможности или настраиваемое расписание, сначала настроить эти параметры, с помощью [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md) и [managed_backup.sp_ backup_config_schedule &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md) перед включением управляемое резервное копирование с помощью этой процедуры.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @enable_backup  
 Включает или выключает [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для указанной базы данных. @enable_backup — **Бит**. Обязательный параметр при настройке [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для первого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При изменении существующего [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] конфигурации, этот параметр является необязательным. В этом случае существующие значения сохраняются любые параметры конфигурации не указан.  
  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования на определенной базе данных.  
  
 @container_url  
 URL-адрес, указывающий местоположение резервной копии. Когда @credential_name имеет значение NULL, этот URL-адрес является URL-адрес общего доступа URL-адреса (SAS) в контейнер больших двоичных объектов в службе хранилища Azure, и резервные копии использовать новый возможность резервного копирования на блок больших двоичных объектов. Дополнительные сведения см. в статье [основные сведения о SAS](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/). Когда @credential_name указан, то это URL-адрес учетной записи хранения, а резервные копии использовать устаревшие возможность резервного копирования на странице большого двоичного объекта.  
  
> [!NOTE]  
>  Только URL-адрес SAS поддерживается для этого параметра в настоящее время.  
  
 @retention_days  
 Срок хранения файлов резервной копии в днях. @storage_url — Целое число. Это обязательный параметр при настройке [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в первый раз на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При изменении [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] конфигурации, этот параметр является необязательным. Если аргумент не указан, сохраняются существующие значения конфигурации.  
  
 @credential_name  
 Имя объекта учетных данных SQL, который используется для проверки подлинности учетной записи хранения Windows Azure. @credentail_name — **SYSNAME**. При указании страничный большой двоичный объект хранится резервная копия. Если этот параметр имеет значение NULL, резервная копия будет храниться как большой двоичный объект блока. Резервное копирование на страничный большой двоичный объект является устаревшими, поэтому рекомендуется использовать новые функции резервного копирования большого двоичного объекта блока. При использовании для изменения конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] этот параметр не обязателен. Если не указан, сохраняются существующие значения конфигурации.  
  
> [!WARNING]
>  **@credential_name** Параметр в настоящее время не поддерживается. Поддерживается только резервное копирование в блочные BLOB-объектов, на которой требуется этот параметр, чтобы иметь значение NULL.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в **db_backupoperator** роли базы данных с помощью **ALTER ANY CREDENTIAL** разрешения, и **EXECUTE** разрешения на **sp_delete_ backuphistory** хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 Можно создать контейнер учетной записи хранения и URL-адрес SAS, используя последнюю версию команд Azure PowerShell. В следующем примере создается новый контейнер, mycontainer, в учетную запись хранения mystorageaccount и затем получает URL-адрес SAS для него с полными правами.  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 В следующем примере включается [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для экземпляра SQL Server, в котором выполняется, задает политику хранения до 30 дней, задает в качестве назначения в контейнер с именем «mycontainer» в учетной записи хранения с именем «mystorageaccount».  
  
```Transact-SQL 
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=1  
                ,@container_url = 'https://mystorageaccount.blob.core.windows.net/mycontainer'  
                ,@retention_days=30;   
GO  
  
```
  
 Следующий пример отключает [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для экземпляра SQL Server, в котором выполняется.  
  
```Transact-SQL  
Use msdb;  
Go  
EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=0;  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
