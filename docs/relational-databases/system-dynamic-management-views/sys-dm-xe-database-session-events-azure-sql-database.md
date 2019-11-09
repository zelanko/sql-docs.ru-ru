---
title: sys. dm_xe_database_session_events
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 9e985a19-f93f-4c56-b644-12c529298011
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-lt-2019
ms.openlocfilehash: 82018dc0aec7083df712e73bfb0a58c13c144f89
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844480"
---
# <a name="sysdm_xe_database_session_events-azure-sql-database"></a>sys.dm_xe_database_session_events (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о событиях сеанса. События представляют собой дискретные точки выполнения. Предикаты можно применять к событиям, чтобы остановить их запуск, если событие не содержит необходимых данных.  
  
||  
|-|  
|Область **применения**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и все более поздние версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|Адрес сеанса событий в памяти. Не допускает значение NULL.|  
|event_name|**nvarchar(60)**|Имя события, к которому привязано действие. Не допускает значение NULL.|  
|event_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится событие. Не допускает значение NULL.|  
|event_predicate|**nvarchar (2048)**|XML-представление дерева предиката, применяемого к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|sys. dm_xe_database_session_events. event_session_address|sys. dm_xe_database_sessions. Address|«многие к одному»|  
|sys. dm_xe_database_session_events. event_package_guid, sys. dm_xe_database_session_events. event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|«многие к одному»|  
  
  
