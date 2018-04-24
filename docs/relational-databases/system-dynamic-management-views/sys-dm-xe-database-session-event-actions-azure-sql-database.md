---
title: sys.dm_xe_database_session_event_actions (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a1a7f35f009cde911ce104ce80d00f1b705cfe65
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="sysdmxedatabasesessioneventactions-azure-sql-database"></a>sys.dm_xe_database_session_event_actions (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о действиях сеанса событий. Действия выполняются, когда происходят события. В этом административном представлении собраны статистические данные о количестве выполнений действия и общем времени выполнения этого действия.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и всем последующим версиям.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Адрес сеанса событий в памяти. Не допускает значение NULL.|  
|action_name|**nvarchar(60)**|Имя действия. Не допускает значение NULL.|  
|action_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, который содержит это действие. Не допускает значение NULL.|  
|event_name|**nvarchar(60)**|Имя события, для которого предназначено действие. Не допускает значение NULL.|  
|event_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, который содержит это событие. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_event_actions.event_session_address|sys.dm_xe_database_sessions.address|«многие к одному»|  
|sys.dm_xe_database_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_database_session_events.event_package_guid|«многие к одному»|  
|sys.dm_xe_database_session_event_actions.event_name<br /><br /> sys.dm_xe_database_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
