---
title: sys.dm_cryptographic_provider_algorithms (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_algorithms_TSQL
- sys.dm_cryptographic_provider_algorithms
- sys.dm_cryptographic_provider_algorithms_TSQL
- dm_cryptographic_provider_algorithms
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_algorithms dynamic management function
ms.assetid: 8bcccb37-5cfb-4e1e-a0bb-7ff4c279fe8e
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 245732520f51f520f063b5117e92c9e4bc448eeb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmcryptographicprovideralgorithms-transact-sql"></a>sys.dm_cryptographic_provider_algorithms (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает алгоритмы, поддерживаемые поставщиком расширенного управления ключами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_cryptographic_provider_algorithms ( provider_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_id*  
 Идентификационный номер поставщика расширенного управления ключами, без значения по умолчанию.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|algorithm_id|**int**|Идентификатор алгоритма.|  
|algorithm_tag|**nvarchar(60)**|Тег идентификации алгоритма.|  
|key_type|**nvarchar(128)**|Показывает тип ключа. Может принимать значение ASYMMETRIC KEY либо SYMMETRIC KEY.|  
|key_length|**int**|Отображает длину ключа в битах.|  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом роли базы данных public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируются параметры поставщика с идентификатором `1234567`.  
  
```  
SELECT * FROM sys.dm_cryptographic_provider_algorithms(1234567);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Динамические представления управления и функции, связанные с безопасностью (Transact-SQL)](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
