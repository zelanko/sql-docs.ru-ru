---
description: managed_backup. sp_backup_config_advanced (Transact-SQL)
title: managed_backup. sp_backup_config_advanced (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d092851d710de96e9c1b06d2866183a7dfac01bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464696"
---
# <a name="managed_backupsp_backup_config_advanced-transact-sql"></a>managed_backup. sp_backup_config_advanced (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Настраивает дополнительные параметры для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a> Аргументы  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования в определенной базе данных. Если задано значение NULL или *, то эта управляемая резервная копия применяется ко всем базам данных на сервере.  
  
 @encryption_algorithm  
 Имя алгоритма шифрования, используемого во время резервного копирования для шифрования файла резервной копии. @encryption_algorithmАргумент имеет тип **sysname**. Это обязательный параметр при настройке конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в первый раз для базы данных. Укажите **NO_ENCRYPTION** , если вы не хотите шифровать файл резервной копии. При изменении [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] параметров конфигурации этот параметр является необязательным. Если параметр не указан, существующие значения конфигурации сохраняются. Разрешенные значения для этого параметра:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Дополнительные сведения об алгоритмах шифрования см. в разделе [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Тип шифратора, который может быть либо "CERTIFICATE", либо "ASYMMETRIC_KEY". Параметр @encryptor_type имеет тип **nvarchar (32)**. Этот параметр является необязательным, если для параметра задано значение NO_ENCRYPTION @encryption_algorithm .  
  
 @encryptor_name  
 Имя существующего сертификата или асимметричного ключа для шифрования резервной копии. @encryptor_nameАргумент имеет тип **sysname**. При использовании асимметричного ключа он должен быть сконфигурирован поставщиком расширенного управления ключами (EKM). Этот параметр является необязательным, если для параметра задано значение NO_ENCRYPTION @encryption_algorithm .  
  
 Дополнительные сведения см. в разделе [Расширенное управление ключами &#40;Расширенный поиск ключей&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 @local_cache_path  
 Этот параметр пока не поддерживается.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных **db_backupoperator** , с разрешениями **ALTER ANY CREDENTIAL** и **EXECUTE** для хранимой процедуры **sp_delete_backuphistory** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере задаются дополнительные параметры конфигурации для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] экземпляра SQL Server.  
  
```sql
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
