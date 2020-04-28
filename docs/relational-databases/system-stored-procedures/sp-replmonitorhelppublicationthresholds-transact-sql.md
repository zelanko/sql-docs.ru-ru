---
title: sp_replmonitorhelppublicationthresholds (T-SQL)
description: Описывает sp_replmonitorhelppublicationthresholds хранимую процедуру, которая возвращает пороговые метрики, заданные для отслеживаемой публикации.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
author: stevestein
ms.author: sstein
ms.openlocfilehash: d351db8ca696263f294f5a52f364d42ac48bad24
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75320781"
---
# <a name="sp_replmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает пороговые показатели, заданные для контролируемой публикации. Эта хранимая процедура, используемая для наблюдения за репликацией, выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorhelppublicationthresholds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя опубликованной базы данных. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication_type = ] publication_type`Тип публикации. *publication_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Публикация транзакций.|  
|**1**|Публикация моментальных снимков.|  
|**2**|Публикация слиянием.|  
|NULL (по умолчанию)|Репликация пытается определить тип публикации.|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Идентификатор метрики быстродействия репликации, который может иметь одно из таких значений.<br /><br /> **1expiration** — следит за приближением истечения срока подписки на публикации транзакций.<br /><br /> **2latency** — отслеживает производительность подписок на публикации транзакций.<br /><br /> **4mergeexpiration** — следит за приближающимся истечением срока подписки на публикации слиянием.<br /><br /> **5mergeslowrunduration** — отслеживает продолжительность синхронизации слиянием через подключения с низкой пропускной способностью (коммутируемое подключение).<br /><br /> **6mergefastrunduration** — отслеживает продолжительность синхронизации слиянием через подключения с высокой пропускной СПОСОБНОСТЬЮ (локальная сеть).<br /><br /> **7mergefastrunspeed** — следит за частотой синхронизации слиянием через подключения с высокой пропускной СПОСОБНОСТЬЮ (локальная сеть).<br /><br /> **8mergeslowrunspeed** — следит за частотой синхронизации слиянием через подключения с низкой пропускной способностью (коммутируемое подключение).|  
|**title**|**sysname**|Имя метрики производительности репликации.|  
|**value**|**int**|Пороговое значение метрики производительности.|  
|**shouldalert**|**bit**|Имеет значение, если предупреждение должно быть создано, если метрика превышает заданное пороговое значение для данной публикации; значение **1** указывает, что должно быть создано предупреждение.|  
|**IsEnabled**|**bit**|Если для этой публикации включено наблюдение для этой метрики производительности репликации; значение **1** указывает, что мониторинг включен.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_replmonitorhelppublicationthresholds** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли базы данных **db_owner** или **replmonitor** в базе данных распространителя могут выполнять **sp_replmonitorhelppublicationthresholds**.  
  
## <a name="see-also"></a>См. также:  
 [Программный мониторинг репликации](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
