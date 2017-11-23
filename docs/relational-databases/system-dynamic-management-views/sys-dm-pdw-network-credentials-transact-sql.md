---
title: "sys.dm_pdw_network_credentials (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.reviewer: 
ms.service: 
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 21935bde6ebefe2b30743a4961ba05e3092539d6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Возвращает список всех сетевые учетные данные хранятся в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] устройства для всех целевых серверов. Для узла элемента управления, а каждый вычислительный узел выводятся результаты.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
|имя_сервера_назначения|**nvarchar(32)**|IP-адрес целевого сервера, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] будет обращаться к учетным данным пользователя и пароль.|  
|username|**nvarchar(32)**|Имя пользователя, для которого он сохраняется.|  
|last_modified|**datetime**|Дата и время последней операции изменения учетных данных.|  
  
## <a name="permissions"></a>Permissions  
 Требуется VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Общие замечания  
 Ключ для данного динамического административного представления *pdw_node_id* , а также *имя_сервера_назначения*.  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
