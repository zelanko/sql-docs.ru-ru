---
title: sys.dm_cryptographic_provider_keys (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_cryptographic_provider_keys_TSQL
- dm_cryptographic_provider_keys_TSQL
- dm_cryptographic_provider_keys
- sys.dm_cryptographic_provider_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_keys dynamic management function
ms.assetid: 5a8c1421-c56b-44b5-96e5-4f01782a0c7c
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00a6af646b83c1f928dc9a6c790ab0033518436e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmcryptographicproviderkeys-transact-sql"></a>sys.dm_cryptographic_provider_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о ключах, предоставленных поставщиком расширенного управления ключами.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dm_cryptographic_provider_keys ( provider_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_id*  
 Идентификационный номер поставщика расширенного управления ключами, без значения по умолчанию.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**key_id**|**int**|Идентификатор ключа на поставщике.|  
|**key_name**|**nvarchar(512)**|Имя ключа на поставщике.|  
|**key_thumbprint**|**varbinary(32)**|Отпечаток с поставщика ключа.|  
|**algorithm_id**|**int**|Идентификатор алгоритма на поставщике.|  
|**algorithm_tag**|**int**|Тег алгоритма на поставщике.|  
|**key_type**|**nchar(256)**|Тип ключа на поставщике.|  
|**key_length**|**int**|Длина ключа на поставщике.|  
  
## <a name="permissions"></a>Разрешения  
 При запросе к этому представлению выполняется проверка подлинности контекста пользователя на поставщике расширенного управления ключами и перечисление всех ключей, видимых для пользователя.  
  
 Если проверку подлинности пользователя на поставщике расширенного управления ключами выполнить не удалось, данные ключей не возвращаются.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируются свойства ключа для поставщика с идентификатором `1234567`.  
  
```  
SELECT * FROM sys.dm_cryptographic_provider_keys(1234567);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  
