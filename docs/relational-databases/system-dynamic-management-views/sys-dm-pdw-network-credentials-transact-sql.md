---
description: sys.dm_pdw_network_credentials (Transact-SQL)
title: sys.dm_pdw_network_credentials (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 7d94853e62c1e9e97ddd65ad973e9e481d90bcb0
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472745"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Возвращает список всех сетевых учетных данных, хранящихся в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] устройстве для всех целевых серверов. Результаты перечисляются для узла управления и каждого из вычислений.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
|target_server_name|**nvarchar(32)**|IP-адрес целевого сервера, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] доступ к которому будет осуществляться с помощью учетных данных пользователя и пароля.|  
|username|**nvarchar(32)**|Имя пользователя, для которого хранится пароль.|  
|last_modified|**datetime**|Дата и время последней операции, которая изменила учетные данные.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется представление состояния сервера.  
  
## <a name="general-remarks"></a>Общие замечания  
 Ключ для этого динамического административного представления *pdw_node_id* и *target_server_name*.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
