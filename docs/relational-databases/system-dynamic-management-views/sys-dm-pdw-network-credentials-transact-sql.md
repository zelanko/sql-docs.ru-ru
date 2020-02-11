---
title: sys. dm_pdw_network_credentials (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b75eb53da9961025e3310f27e4a12608dd4fda78
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899362"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>sys. dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Возвращает список всех сетевых учетных данных, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] хранящихся в устройстве для всех целевых серверов. Результаты перечисляются для узла управления и каждого из вычислений.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
|target_server_name|**nvarchar (32)**|IP-адрес целевого сервера, доступ [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] к которому будет осуществляться с помощью учетных данных пользователя и пароля.|  
|Имя пользователя|**nvarchar (32)**|Имя пользователя, для которого хранится пароль.|  
|last_modified|**datetime**|Дата и время последней операции, которая изменила учетные данные.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется представление состояния сервера.  
  
## <a name="general-remarks"></a>Общие замечания  
 Ключ для этого динамического административного представления *pdw_node_id* и *target_server_name*.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
