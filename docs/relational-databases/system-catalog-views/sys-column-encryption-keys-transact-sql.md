---
description: sys. column_encryption_keys (Transact-SQL)
title: sys. column_encryption_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_encryption_keys
- column_encryption_keys_TSQL
- sys.column_encryption_keys_TSQL
- column_encryption_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_keys catalog view
ms.assetid: 43980dd8-b9b1-4869-a304-2c183ae8977d
author: jaszymas
ms.author: jaszymas
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5792aac11b14077430846a893b811eff8b617fc2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469960"
---
# <a name="syscolumn_encryption_keys--transact-sql"></a>sys. column_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-xxx-md.md)]

  Возвращает сведения о ключах шифрования столбцов (Цекс), созданных с помощью инструкции [CREATE Column Encryption Key](../../t-sql/statements/create-column-encryption-key-transact-sql.md) . Каждая строка представляет CEK.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя CMK.|  
|**column_encryption_key_id**|**int**|Идентификатор CEK.|  
|**create_date**|**datetime**|Дата создания CEK.|  
|**modify_date**|**datetime**|Дата последнего изменения CEK.|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения на **Просмотр любого столбца с ключом шифрования** .  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Создание ключа шифрования СТОЛБЦА &#40;&#41;Transact-SQL ](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ИЗМЕНЕНИЕ ключа шифрования СТОЛБЦА &#40;языке Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [УДАЛИТЬ ключ шифрования СТОЛБЦА &#40;&#41;Transact-SQL ](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [Создание главного ключа СТОЛБЦА &#40;&#41;Transact-SQL ](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted с безопасным енклавес](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Общие сведения об управлении ключами для Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)    

  
  
