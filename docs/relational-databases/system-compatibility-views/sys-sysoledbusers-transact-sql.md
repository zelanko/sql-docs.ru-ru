---
title: sys. таблицу sysoledbusers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
author: rothja
ms.author: jroth
ms.openlocfilehash: d7c8b97a04e8b9898a9d49a412c5c6e5a2aa910c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68076535"
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Эта системная таблица [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] включена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве представления только для обеспечения обратной совместимости. Вместо этого рекомендуется использовать [представления каталога](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) .  
  
 Содержит по одной строке для каждой пары пользователя и пароля для указанного связанного сервера. **таблицу sysoledbusers** хранится в базе данных **master** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|Идентификатор защиты (SID) сервера.|  
|**rmtloginame**|**nvarchar (** 128 **)**|Имя удаленного входа, которое **логинсид** сопоставляется для связанных **рмтсервид**.|  
|**rmtpassword**|**nvarchar (** 128 **)**|Возвращает значение NULL.|  
|**логинсид**|**varbinary (** 85 **)**|Идентификатор SID локального имени входа для сопоставления.|  
|**status**|**smallint**|Если значение равно 1, то при сопоставлении необходимо использовать учетные данные пользователя.|  
|**changedate**|**datetime**|Дата последнего изменения сведений о сопоставлении.|  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
