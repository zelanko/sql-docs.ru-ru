---
description: sys.column_master_keys (Transact-SQL)
title: sys.column_master_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/15/2019
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
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9b62a54ec2ab17d76f5f726dbd26f28a60d79afc
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97429649"
---
# <a name="syscolumn_master_keys-transact-sql"></a>sys.column_master_keys (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Возвращает по одной строке для каждого главного ключа базы данных, добавленного с помощью инструкции [создания главного ключа](../../t-sql/statements/create-column-master-key-transact-sql.md) . Каждая строка представляет один главный ключ столбца (CMK).  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя CMK.|  
|**column_master_key_id**|**int**|Идентификатор главного ключа столбца.|  
|**create_date**|**datetime**|Дата создания главного ключа столбца.|  
|**modify_date**|**datetime**|Дата последнего изменения главного ключа столбца.|  
|**key_store_provider_name**|**sysname**|Имя поставщика для хранилища главных ключей столбцов, содержащего CMK. Допустимыми значениями являются:<br /><br /> MSSQL_CERTIFICATE_STORE — если хранилищем главных ключей столбцов является хранилище сертификатов.<br /><br /> Определяемое пользователем значение, если хранилище главных ключей столбцов имеет настраиваемый тип.|  
|**key_path**|**nvarchar(4000)**|Путь к главному столбцу главного ключа, относящийся к ключу. Формат пути зависит от типа хранилища главных ключей столбцов. Пример.<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Для пользовательского хранилища главного ключа столбца разработчик несет ответственность за определение пути к ключу для пользовательского хранилища главного ключа столбца.|  
|**allow_enclave_computations**|**bit**|Указывает, можно ли использовать главный ключ столбца анклава (если ключи шифрования столбца, зашифрованные с помощью этого главного ключа, могут использоваться для вычислений в защищенном енклавес на стороне сервера). Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).|  
|**подпись**|**varbinary(max)**|Цифровая подпись **key_path** и **allow_enclave_computations**, созданная с помощью главного ключа столбца, на которую ссылается **key_path**.|


  
## <a name="permissions"></a>Разрешения  
 Требует разрешения на **Просмотр любого столбца в главном ключе** .  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Общие сведения об управлении ключами для Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
 
  
  
