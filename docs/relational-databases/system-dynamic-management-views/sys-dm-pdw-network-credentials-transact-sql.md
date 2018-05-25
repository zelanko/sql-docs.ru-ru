---
title: sys.dm_pdw_network_credentials (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e7b4534410eabf1186b115c07fef8a8d79960938
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Возвращает список всех сетевые учетные данные хранятся в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] устройства для всех целевых серверов. Для узла элемента управления, а каждый вычислительный узел выводятся результаты.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
|имя_сервера_назначения|**nvarchar(32)**|IP-адрес целевого сервера, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] будет обращаться к учетным данным пользователя и пароль.|  
|username|**nvarchar(32)**|Имя пользователя, для которого он сохраняется.|  
|last_modified|**datetime**|Дата и время последней операции изменения учетных данных.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Общие замечания  
 Ключ для данного динамического административного представления *pdw_node_id* , а также *имя_сервера_назначения*.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
