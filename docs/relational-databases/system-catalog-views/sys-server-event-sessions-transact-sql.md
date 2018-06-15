---
title: sys.server_event_sessions (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_event_sessions
- server_event_sessions_TSQL
- sys.server_event_sessions_TSQL
- sys.server_event_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_sessions catalog view
- xe
ms.assetid: 796f3093-6a3e-4d67-8da6-b9810ae9ef5b
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 06f4385e35efe104bf83f98ef325a6d51e960df8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222025"
---
# <a name="sysservereventsessions-transact-sql"></a>sys.server_event_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перечисляет все определения сеанса событий, которые существуют в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Уникальный идентификатор сеанса событий. Не допускает значение NULL.|  
|имя|**sysname**|Определяемое пользователем имя, идентифицирующее сеанс событий. имя является уникальным. Не допускает значение NULL.|  
|event_retention_mode|**nchar(1)**|Определяет способ обработки потери события. Значение по умолчанию — S. Не допускает значения NULL. Принимает одно из следующих значений.<br /><br /> Х. Соответствует event_retention_mode_desc = allow_single_event_loss.<br /><br /> Н. Соответствует event_retention_mode_desc = allow_multiple_event_loss.<br /><br /> О. Соответствует event_retention_mode_desc = NO_EVENT_LOSS|  
|event_retention_mode_desc|**sysname**|Описывает способ обработки потери события. Значение по умолчанию ALLOW_SINGLE_EVENT_LOSS. Не допускает значение NULL. Принимает одно из следующих значений.<br /><br /> ALLOW_SINGLE_EVENT_LOSS. Возможна потеря событий в сеансе. Одиночные события удаляются только в том случае, если все буферы событий полны. Потеря одиночных событий при заполнении буферов событий обеспечивает приемлемые характеристики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одновременно уменьшая до минимума потери данных в потоке обработанных событий.<br /><br /> ALLOW_MULTIPLE_EVENT_LOSS. Возможна потеря полных буферов событий в сеансе. Число потерянных событий зависит от размера памяти, выделенной для сеанса, способа секционирования памяти и размера событий в буфере. Этот параметр уменьшает влияние быстрого заполнения буферов событий на производительность сервера. Однако возможна потеря большого числа событий в сеансе.<br /><br /> NO_EVENT_LOSS. Потеря событий не разрешена. Этот параметр обеспечивает сохранение всех произошедших событий. При использовании этого параметра все задачи, которые инициируют события, должны ждать освобождения пространства в буфере событий. Это может привести к заметному снижению производительности во время активного сеанса событий.|  
|max_dispatch_latency|**int**|Промежуток времени в миллисекундах, в течение которого события находятся в буферной памяти перед отправкой целям сеанса. Допустимые значения: от 1 до 2 147 483 648 и -1. Значение «-1» указывает на то, что задержка диспетчера является бесконечной. Допускает значение NULL.|  
|max_memory|**int**|Объем памяти, выделенной в сеансе для буферов событий. Значение по умолчанию — 4 МБ. Допускает значение NULL.|  
|max_event_size|**int**|Объем памяти, выделенной для событий, которые не могут уместиться в буферах сеанса событий. Если значение max_event_size превышает расчетный размер буфера, два дополнительных буфера размера max_event_size выделяются для сеанса событий. Допускает значение NULL.|  
|memory_partition_mode|**nchar(1)**|Местоположение в памяти, в котором созданы буферы событий. Режим раздела памяти по умолчанию — G. Не допускает значения NULL. memory_partition_mode является одним из следующих:<br /><br /> G — NONE;<br /><br /> C — PER_CPU;<br /><br /> N — PER_NODE.|  
|memory_partition_mode_desc|**sysname**|По умолчанию значение установлено в NONE. Не допускает значение NULL. Принимает одно из следующих значений.<br /><br /> NONE. Внутри экземпляра SQL Server создается один набор буферов.<br /><br /> PER_CPU. Набор буферов создается для каждого ЦП.<br /><br /> PER_NODE. Набор буферов создается для каждого узла неоднородного доступа к памяти (NUMA).|  
|track_causality|**бит**|Включает или отключает отслеживание причинности. Если установлено значение 1 (ВКЛ.), то отслеживание включено и можно установить соответствие между связанными событиями в различных серверных соединениях. Значение по умолчанию — 0 (ВЫКЛ.). Не допускает значение NULL.|  
|startup_state|**бит**|Значение определяет, запускается ли сеанс автоматически при запуске сервера. Значение по умолчанию равно 0. Не допускает значение NULL. Может принимать одно из следующих значений:<br /><br /> 0 (ВЫКЛ.). Сеанс не запускается автоматически при запуске сервера.<br /><br /> 1 (ВКЛ.). Сеанс событий запускается при запуске сервера.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога расширенных событий (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
