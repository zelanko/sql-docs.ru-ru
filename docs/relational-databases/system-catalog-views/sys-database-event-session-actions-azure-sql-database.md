---
title: "sys.database_event_session_actions (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: 
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 594515b901a0b8c284ef81fd5a426094e17a74d4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseeventsessionactions-azure-sql-database"></a>sys.database_event_session_actions (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого действия над каждым событием из сеанса событий.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и все более поздние версии.|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Идентификатор сеанса событий. Не допускает значение NULL.|  
|event_id|**int**|Идентификатор события. Этот идентификатор уникален внутри объекта сеанса событий. Не допускает значение NULL.|  
|имя|**sysname**|Имя действия. Допускает значение NULL.|  
|пакет|**sysname**|Имя пакета событий, который содержит событие. Допускает значение NULL.|  
|module|**sysname**|Имя модуля, который содержит событие. Допускает значение NULL.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  
  
## <a name="remarks"></a>Замечания  
 Это представление имеет следующее количество элементов связей.  
  
||||  
|-|-|-|  
|От|Чтобы|Связь|  
|sys.database_event_session_actions.event_session_id|sys.sys.database_event_sessions.event_session_id|Многие к одному|  
|sys.database_event_session_actions.event_id<br /><br /> sys.database_event_session_actions.event_session_id|sys.database_event_session_events.event_session_id<br /><br /> sys.database_event_session_events.event_id|Многие к одному|  
  
  
