---
title: sys.database_event_session_events (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e0e3d1035488696697d2f717e888806fb352b187
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707212"
---
# <a name="sysdatabaseeventsessionevents-azure-sql-database"></a>sys.database_event_session_events (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого события в сеансе событий.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] версии 12 и любые более поздние версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Идентификатор сеанса событий. Не допускает значение NULL.|  
|event_id|**int**|Идентификатор события. Этот идентификатор уникален внутри объекта сеанса событий. Не допускает значение NULL.|  
|name|**sysname**|Имя события. Не допускает значение NULL.|  
|пакет|**sysname**|Имя пакета событий, который содержит событие. Не допускает значение NULL.|  
|module|**sysname**|Имя модуля, который содержит событие. Не допускает значение NULL.|  
|predicate|**nvarchar(3000)**|Выражение предиката, применяемое к событию. Допускает значение NULL.|  
|predicate_xml|**nvarchar(3000)**|Выражение предиката XML, применяемое к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  
  
## <a name="remarks"></a>Примечания  
 Это представление имеет следующее количество элементов связей.  
  
||||  
|-|-|-|  
|От|Чтобы|Связь|  
|sys.database_event_session_events.event_session_id|sys.database_event_sessions.event_session_id|Многие к одному|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
