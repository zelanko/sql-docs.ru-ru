---
description: sys.database_event_session_events (база данных SQL Azure)
title: sys. database_event_session_events (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c6234e6b9c6cc2cfeb48b01fd2a2541ec2244678
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646354"
---
# <a name="sysdatabase_event_session_events-azure-sql-database"></a>sys.database_event_session_events (база данных SQL Azure)
[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Возвращает строку для каждого события в сеансе событий.  
  
||  
|-|  
|**Применимо к**версии [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 12 и всем более поздним версиям.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Идентификатор сеанса событий. Не допускает значение NULL.|  
|event_id|**int**|Идентификатор события. Этот идентификатор уникален внутри объекта сеанса событий. Не допускает значение NULL.|  
|name|**sysname**|Имя события. Не допускает значение NULL.|  
|пакет|**sysname**|Имя пакета событий, который содержит событие. Не допускает значение NULL.|  
|module|**sysname**|Имя модуля, который содержит событие. Не допускает значение NULL.|  
|predicate|**nvarchar (3000)**|Выражение предиката, применяемое к событию. Допускает значение NULL.|  
|predicate_xml|**nvarchar (3000)**|Выражение предиката XML, применяемое к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  
  
## <a name="remarks"></a>Комментарии  
 Это представление имеет следующее количество элементов связей.  
  
| От | Кому | Связь |
| ---- | -- | ------------ |
|sys. database_event_session_events. event_session_id|sys. database_event_sessions. event_session_id|Многие к одному|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
