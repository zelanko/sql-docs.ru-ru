---
title: sys. openkeys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- openkeys_TSQL
- sys.openkeys_TSQL
- openkeys
- sys.openkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.openkeys catalog view
ms.assetid: 719a1259-2398-4fcb-ba05-aeabba7aec21
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f1ef2a7b5bdff79c3d12441f09ab2a05439f7a61
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125382"
---
# <a name="sysopenkeys-transact-sql"></a>sys.openkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Это представление каталога возвращает сведения о ключах шифрования, открытых в текущем сеансе.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, содержащей ключ.|  
|**database_name**|**sysname**|Имя базы данных, содержащей ключ.|  
|**key_id**|**int**|Идентификатор ключа. Идентификатор уникален в пределах базы данных.|  
|**key_name**|**sysname**|Имя ключа. Уникально в пределах базы данных.|  
|**key_guid**|**varbinary**|Идентификатор GUID ключа. Уникально в пределах базы данных.|  
|**opened_date**|**datetime**|Дата и время открытия ключа.|  
|**status**|**int**|1, если ключ действителен в метаданных. 0, если ключ не найден в метаданных.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md)  
  
  
