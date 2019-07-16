---
title: sys.dm_xe_database_session_events (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 9e985a19-f93f-4c56-b644-12c529298011
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9021696dc819fb37a317d8dfea0d193333ced278
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090435"
---
# <a name="sysdmxedatabasesessionevents-azure-sql-database"></a>sys.dm_xe_database_session_events (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о событиях сеанса. События представляют собой дискретные точки выполнения. Предикаты можно применять к событиям, чтобы остановить их запуск, если событие не содержит необходимых данных.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] До версии 12 и любые более поздние версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Адрес сеанса событий в памяти. Не допускает значение NULL.|  
|event_name|**nvarchar(60)**|Имя события, к которому привязано действие. Не допускает значение NULL.|  
|event_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится событие. Не допускает значение NULL.|  
|event_predicate|**nvarchar(2048)**|XML-представление дерева предиката, применяемого к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|«многие к одному»|  
|sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|«многие к одному»|  
  
  
