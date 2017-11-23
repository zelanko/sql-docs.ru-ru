---
title: "sys.dm_database_encryption_keys (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bb177f781bee54b908624e1f940c12d5bdaf5a13
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdatabaseencryptionkeys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о состоянии шифрования базы данных и о связанных ключах шифрования базы данных. Дополнительные сведения о шифровании баз данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|  
|encryption_state|**int**|Указывает, является ли база данных зашифрованной или незашифрованной.<br /><br /> 0 = нет ключа шифрования базы данных, нет шифрования<br /><br /> 1 = не зашифрована<br /><br /> 2 = выполняется шифрование<br /><br /> 3 = зашифрована<br /><br /> 4 = выполняется изменение ключа<br /><br /> 5 = выполняется расшифровка<br /><br /> 6 = производится изменение защиты (изменился сертификат или асимметричный ключ, которым зашифрован ключ шифрования базы данных).|  
|create_date|**datetime**|Отображает дату создания ключа шифрования.|  
|regenerate_date|**datetime**|Отображает дату повторного создания ключа шифрования.|  
|modify_date|**datetime**|Отображает дату изменения ключа шифрования.|  
|set_date|**datetime**|Отображает дату применения ключа шифрования к базе данных.|  
|opened_date|**datetime**|Показывает, когда ключ базы данных был открыт в последний раз.|  
|key_algorithm|**nvarchar(32)**|Отображает алгоритм, используемый для ключа.|  
|key_length|**int**|Отображает длину ключа.|  
|encryptor_thumbprint|**varbinary(20)**|Показывает отпечаток шифратора.|  
|encryptor_type|**nvarchar(32)**|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Описывает шифратор.|  
|percent_complete|**real**|Процент выполнения шифрования базы данных. Значение 0, если изменения состояния не было.|  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
  
## <a name="see-also"></a>См. также:  

 [Динамические административные представления и функции, связанные с безопасностью (Transact-SQL)](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Ключи шифрования базы данных и SQL Server (компонент Database Engine)](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [СОЗДАТЬ ключ ШИФРОВАНИЯ базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ИЗМЕНИТЬ ключ ШИФРОВАНИЯ базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
