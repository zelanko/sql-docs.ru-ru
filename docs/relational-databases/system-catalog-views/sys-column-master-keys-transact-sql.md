---
title: sys.column_master_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
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
ms.openlocfilehash: 1cb1740bdb0ae26d91e2a9ad9e2becb69d3b2810
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013711"
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
|**key_store_provider_name**|**sysname**|Имя поставщика хранилища главных ключей столбцов, который содержит ключ CMK. Допустимые значения:<br /><br /> MSSQL_CERTIFICATE_STORE - Если Store сертификат хранилища главных ключей столбцов.<br /><br /> Определяемое пользователем значение, если хранилища главных ключей столбца пользовательского типа.|  
|**key_path**|**nvarchar(4000)**|Путь конкретного хранилища главного ключа столбца ключа. Формат пути зависит от типа хранилища главного ключа столбца. Пример<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Для хранилища главных ключей пользовательских столбцов, разработчик отвечает за определение — какие путь к ключу для хранилища главных ключей пользовательского столбца.|  
|**allow_enclave_computations**|**bit**|Указывает, является ли главный ключ столбца поддержкой анклава, (если ключ шифрования столбца, зашифрованный с помощью этого главного ключа, может использоваться для вычислений внутри безопасного enclaves на стороне сервера). Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).|  
|**signature**|**varbinary(max)**|Цифровую подпись **key_path** и **allow_enclave_computations**, созданных с помощью главного ключа столбца, ссылается **key_path**.|


  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW ANY COLUMN MASTER KEY** разрешение.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
