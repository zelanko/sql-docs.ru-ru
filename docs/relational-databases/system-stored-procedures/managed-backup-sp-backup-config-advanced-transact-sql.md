---
title: managed_backup.sp_backup_config_advanced (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_optional
- sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional
dev_langs:
- TSQL
helpviewer_keywords:
- sp_backup_config_optional
- managed_backup.sp_backup_config_optional
ms.assetid: 4fae8193-1f88-48fd-a94a-4786efe8d6af
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c3f19fed072e693de6bbebb53354eae8c0bfaa0e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827912"
---
# <a name="managedbackupspbackupconfigadvanced-transact-sql"></a>managed_backup.sp_backup_config_advanced (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Настраивает дополнительные параметры для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования на определенной базе данных. Если значение равно NULL или *, то этот управляемого резервного копирования применяется ко всем базам данных на сервере.  
  
 @encryption_algorithm  
 Имя алгоритма шифрования, используемого во время резервного копирования для шифрования файла резервной копии. @encryption_algorithm — **SYSNAME**. Это обязательный параметр при настройке конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в первый раз для базы данных. Укажите **NO_ENCRYPTION** Если шифровать файл резервной копии не требуется. При изменении параметров конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] этот параметр не обязателен; если он не указан, сохраняются существующие значения. Разрешенные значения для этого параметра:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Дополнительные сведения об алгоритмах шифрования см. в разделе [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Тип шифратора, который может быть либо «СЕРТИФИКАТ» или "ASYMMETRIC_KEY». @encryptor_type — **Nvarchar(32)**. Этот параметр является необязательным, если указано значение NO_ENCRYPTION для @encryption_algorithm параметра.  
  
 @encryptor_name  
 Имя существующего сертификата или асимметричного ключа для шифрования резервной копии. @encryptor_name — **SYSNAME**. При использовании асимметричного ключа он должен быть сконфигурирован поставщиком расширенного управления ключами (EKM). Этот параметр является необязательным, если указано значение NO_ENCRYPTION для @encryption_algorithm параметра.  
  
 Дополнительные сведения см. в статье [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 @local_cache_path  
 Этот параметр не поддерживается.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в **db_backupoperator** роли базы данных с помощью **ALTER ANY CREDENTIAL** разрешения, и **EXECUTE** разрешения на **sp_delete_ backuphistory** хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере задается Дополнительные параметры конфигурации для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для экземпляра SQL Server.  
  
```  
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
