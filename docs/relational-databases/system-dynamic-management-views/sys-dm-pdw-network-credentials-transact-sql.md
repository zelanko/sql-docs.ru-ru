---
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7d9e18284ac4d97efaa217802682fe79ebb2dfc5
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041525"
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Возвращает список всех сетевые учетные данные хранятся в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] устройство для всех целевых серверов. Результаты отображаются в управляющем узле и каждом вычислительном узле.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
|имя_сервера_назначения|**nvarchar(32)**|IP-адрес целевого сервера, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] обратится к с использованием учетных данных имени пользователя и пароля.|  
|username|**nvarchar(32)**|Имя пользователя, для которого хранится пароль.|  
|last_modified|**datetime**|Дата и время последней операции изменения учетных данных.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Общие замечания  
 Ключ для данного динамического административного представления *pdw_node_id* , а также *имя_сервера_назначения*.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
