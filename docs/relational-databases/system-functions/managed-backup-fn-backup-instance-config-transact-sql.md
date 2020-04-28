---
title: managed_backup. fn_backup_instance_config (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_backup_instance_config
- smart_admin.fn_backup_instance_config_TSQL
- fn_backup_instance_config_TSQL
- smart_admin.fn_backup_instance_config
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_instance_config
- fn_backup_instance_config
ms.assetid: 2382a547-c0c9-4e1d-87c9-d8526192eb5a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 41c689d03ebae3afe16dc51d8a47c54e923d3a82
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68067760"
---
# <a name="managed_backupfn_backup_instance_config-transact-sql"></a>managed_backup. fn_backup_instance_config (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает 1 строку с параметрами конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] по умолчанию для экземпляра SQL Server.  
  
 Эта хранимая процедура используется для просмотра или определения текущих параметров конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] по умолчанию для экземпляра SQL Server.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.fn_backup_db_config ()  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Даваемых  
 None  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|is_smart_backup_enabled|INT|Значение 1, если компонент [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] включен, и значение 0, если [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] отключен.|  
|credential_name|SYSNAME|Учетные данные SQL по умолчанию, которые используются для проверки подлинности в хранилище.|  
|retention_days|INT|Срок хранения по умолчанию задается на уровне экземпляра.|  
|storage_url|NVARCHAR (1024)|URL-адрес учетной записи хранения по умолчанию на уровне экземпляра.|  
|encryption_algorithm|SYSNAME|Имя алгоритма шифрования. Если задано значение NULL, шифрование не определено.|  
|encryptor_type|NVARCHAR (32)|Тип используемого шифратора: сертификат или асимметричный ключ. Если задано значение NULL, шифратор не определен.|  
|encryptor_name|SYSNAME|Имя сертификата или асимметричного ключа. Если задано значение NULL, имя не указано|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных **db_backupoperator** с разрешениями **ALTER ANY CREDENTIAL** . Пользователю не следует запрещать разрешение **View ANY DEFINITION** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются параметры конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] по умолчанию для экземпляра, в котором выполняется пример:  
  
```  
Use msdb;  
GO  
SELECT * FROM managed_backup.fn_backup_instance_config ();  
  
```  
  
  
