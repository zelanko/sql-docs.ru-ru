---
title: sys.column_master_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4251ecafad275e64021729abe54fc243d9077f9f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43079727"
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого главного ключа базы данных, добавленных с помощью [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) инструкции. Каждая строка представляет одного главного ключа столбца (CMK).  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя CMK.|  
|**column_master_key_id**|**int**|Идентификатор главного ключа столбца.|  
|**create_date**|**datetime**|Дата создания главного ключа столбца.|  
|**modify_date**|**datetime**|Дата последнего изменения главного ключа столбца.|  
|**key_store_provider_name**|**sysname**|Имя поставщика хранилища главных ключей столбцов, который содержит ключ CMK. Допустимые значения:<br /><br /> MSSQL_CERTIFICATE_STORE — Если Store сертификат хранилища главных ключей столбцов.<br /><br /> Определяемое пользователем значение, если хранилища главных ключей столбца пользовательского типа.|  
|**key_path**|**nvarchar(4000)**|Путь конкретного хранилища главного ключа столбца ключа. Формат пути зависит от типа хранилища главного ключа столбца. Пример<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Для хранилища главных ключей пользовательских столбцов, разработчик отвечает за определение — какие путь к ключу для хранилища главных ключей пользовательского столбца.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW ANY COLUMN MASTER KEY** разрешение.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
