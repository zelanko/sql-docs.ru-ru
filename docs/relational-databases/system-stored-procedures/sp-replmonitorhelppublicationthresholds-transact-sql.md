---
title: sp_replmonitorhelppublicationthresholds, хранимая процедура (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6fd9a16067e4a7a1f670d0d50e1b44ea949208e3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spreplmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ **@publisher**=] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publisher_db**=] **"***publisher_db***"**  
 Имя опубликованной базы данных. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publication_type**=] *publication_type*  
 Тип публикации. *publication_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Публикация транзакций.|  
|**1**|Публикация моментальных снимков.|  
|**2**|Публикация слиянием.|  
|NULL (по умолчанию)|Репликация пытается определить тип публикации.|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Идентификатор метрики быстродействия репликации, который может иметь одно из таких значений.<br /><br /> **1expiration** -следит за приближающимся истечением срока подписки на публикации транзакций.<br /><br /> **2latency** -следит за производительностью подписки на публикации транзакций.<br /><br /> **4mergeexpiration** -следит за приближающимся истечением срока подписки на публикации слиянием.<br /><br /> **5mergeslowrunduration** — следит за продолжительностью синхронизаций слиянием через соединения с низкой пропускной способностью (коммутируемое).<br /><br /> **6mergefastrunduration** — следит за продолжительностью синхронизаций слиянием через соединения с высокой пропускной способностью (локальная сеть).<br /><br /> **7mergefastrunspeed** -следит за частотой синхронизации слиянием через соединения с высокой пропускной способностью (локальная сеть).<br /><br /> **8mergeslowrunspeed** -следит за частотой синхронизации слиянием через соединения с низкой пропускной способностью (коммутируемое).|  
|**title**|**sysname**|Имя метрики производительности репликации.|  
|**value**|**int**|Пороговое значение метрики производительности.|  
|**shouldalert**|**бит**|— Должно быть создано оповещение при превышении порогового значения для этой публикации; значение **1** указывает, должно быть создано предупреждение.|  
|**IsEnabled**|**бит**|— Если мониторинг включен для этой метрики производительности репликации для этой публикации; значение **1** указывает, что наблюдение включено.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_replmonitorhelppublicationthresholds** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** или **replmonitor** предопределенной роли базы данных в базе данных распространителя могут выполнять процедуру **sp_replmonitorhelppublicationthresholds**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
