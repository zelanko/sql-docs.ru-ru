---
title: sys.database_event_session_events (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.service: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1bb0aba27809cbf8588449f4cfe779389585736e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabaseeventsessionevents-azure-sql-database"></a>sys.database_event_session_events (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого события в сеансе событий.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и все более поздние версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Идентификатор сеанса событий. Не допускает значение NULL.|  
|event_id|**int**|Идентификатор события. Этот идентификатор уникален внутри объекта сеанса событий. Не допускает значение NULL.|  
|имя|**sysname**|Имя события. Не допускает значение NULL.|  
|пакет|**sysname**|Имя пакета событий, который содержит событие. Не допускает значение NULL.|  
|module|**sysname**|Имя модуля, который содержит событие. Не допускает значение NULL.|  
|predicate|**nvarchar(3000)**|Выражение предиката, применяемое к событию. Допускает значение NULL.|  
|predicate_xml|**nvarchar(3000)**|Выражение предиката XML, применяемое к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  
  
## <a name="remarks"></a>Замечания  
 Это представление имеет следующее количество элементов связей.  
  
||||  
|-|-|-|  
|От|Чтобы|Связь|  
|sys.database_event_session_events.event_session_id|sys.database_event_sessions.event_session_id|Многие к одному|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
