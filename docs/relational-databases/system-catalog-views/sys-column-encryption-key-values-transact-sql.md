---
title: sys. column_encryption_key_values (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_encryption_key_values
- column_encryption_key_values_TSQL
- sys.column_encryption_key_values
- sys.column_encryption_key_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_key_values catalog view
ms.assetid: 440875ab-b0e9-4966-8c16-01503558fedd
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8c5dc4f2dc42452560162d214844e2264cd0e5e9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73593806"
---
# <a name="syscolumn_encryption_key_values-transact-sql"></a>sys. column_encryption_key_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о зашифрованных значениях ключей шифрования столбцов (Цекс), созданных с помощью инструкции [CREATE Column Encryption Key](../../t-sql/statements/create-column-encryption-key-transact-sql.md) или [ALTER COLUMN Encrypt &#40;инструкций Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md) . Каждая строка представляет значение CEK, зашифрованное с помощью главного ключа столбца (CMK).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_id**|**int**|Идентификатор CEK в базе данных.|  
|**column_master_key_id**|**int**|Идентификатор главного ключа столбца, который использовался для шифрования значения CEK.|  
|**encrypted_value**|**varbinary (8000)**|Значение CEK, зашифрованное с помощью CMK, указанного в column_master_key_id.|  
|**encryption_algorithm_name**|**имеет sysname**|Имя алгоритма, используемого для шифрования значения CEK.<br /><br /> Имя алгоритма шифрования значения. Алгоритм для системных поставщиков должен быть **RSA_OAEP**.|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения на **Просмотр любого столбца с ключом шифрования** .  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание ключа шифрования СТОЛБЦА &#40;&#41;Transact-SQL](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ИЗМЕНЕНИЕ ключа шифрования СТОЛБЦА &#40;языке Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [УДАЛИТЬ ключ шифрования СТОЛБЦА &#40;&#41;Transact-SQL](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [Создание главного ключа СТОЛБЦА &#40;&#41;Transact-SQL](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys. column_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys. column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)   
 [sys. Columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted с безопасным енклавес](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Общие сведения об управлении ключами для Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   

  
  
