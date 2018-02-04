---
title: "sys.dm_xe_database_sessions (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 33ea5179-16bb-4abd-96cc-9bc696e80987
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 85584709967e1ef7988a12389b5b40e30ee47a7d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxedatabasesessions-azure-sql-database"></a>sys.dm_xe_database_sessions (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о событиях сеанса. События представляют собой дискретные точки выполнения. Предикаты можно применять к событиям, чтобы остановить их запуск, если событие не содержит необходимых данных.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и все более поздние версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Адрес сеанса событий в памяти. Не допускает значение NULL.|  
|event_name|**nvarchar(60)**|Имя события, к которому привязано действие. Не допускает значение NULL.|  
|event_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится событие. Не допускает значение NULL.|  
|event_predicate|**nvarchar(2048)**|XML-представление дерева предиката, применяемого к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
Начиная с 2015-07-13 «sys.dm_xe_objects» является одним из этих динамических административных представлений XEvents, которые не содержат «_базы данных» в имени. Опечатка или ошибка в столбце справа в следующей таблице. Имя является одинаковым в Microsoft SQL Server и базы данных SQL Azure. GeneMi.  
  
|От|Чтобы|Связь|  
|--------|------|----------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|«многие к одному»|  
|sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
[Расширенные события в базе данных SQL Azure](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
[Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
 
