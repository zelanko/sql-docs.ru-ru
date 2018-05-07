---
title: sp_replmonitorchangepublicationthreshold (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bfc9b3ad0f67fa462db098a44603cc9cb1a4d586
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spreplmonitorchangepublicationthreshold-transact-sql"></a>sp_replmonitorchangepublicationthreshold (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет пороговые метрики наблюдения за публикацией. Эта хранимая процедура, используемая для наблюдения за репликацией, выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorchangepublicationthreshold [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @metric_id = ] metric_id ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'   
    [ , [ @value = ] value ]   
    [ , [ @shouldalert = ] shouldalert ]   
    [ , [ @mode = ] mode ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publisher** =] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publisher_db** =] **"***publisher_db***"**  
 Имя опубликованной базы данных. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publication** =] **"***публикации***"**  
 Имя публикации, для которой изменяются пороговые атрибуты наблюдения. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publication_type** =] *publication_type*  
 Тип публикации. *publication_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Публикация транзакций.|  
|**1**|Публикация моментальных снимков.|  
|**2**|Публикация слиянием.|  
|NULL (по умолчанию)|Репликация пытается определить тип публикации.|  
  
 [ **@metric_id** =] *metric_id*  
 Идентификатор публикации, изменяемой пороговый показатель. *metric_id* — **int**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Имя метрики|  
|-----------|-----------------|  
|**1**|**expiration** следит за приближающимся истечением срока подписки на публикации транзакций.|  
|**2**|**latency** следит за производительностью подписки на публикации транзакций.|  
|**4**|**mergeexpiration** следит за приближающимся истечением срока подписки на публикации слиянием.|  
|**5**|**mergeslowrunduration** -следит за продолжительностью синхронизаций слиянием через соединения с низкой пропускной способностью (коммутируемое).|  
|**6**|**mergefastrunduration** -следит за продолжительностью синхронизаций слиянием через соединения с высокой пропускной способностью локальной сети (LAN).|  
|**7**|**mergefastrunspeed** — следит за частотой синхронизаций слиянием через соединения с высокой пропускной способностью (локальная сеть).|  
|**8**|**mergeslowrunspeed** -следит за частотой синхронизации слиянием через соединения с низкой пропускной способностью (коммутируемое).|  
  
 Необходимо указать либо *metric_id* или *thresholdmetricname*. Если *thresholdmetricname* указан, то *metric_id* должен иметь значение NULL.  
  
 [ **@thresholdmetricname** =] **"***thresholdmetricname***"**  
 Имя изменяемого порогового показателя публикации. *thresholdmetricname* — **sysname**, значение по умолчанию NULL. Необходимо указать либо *thresholdmetricname* или *metric_id*. Если *metric_id* указан, то *thresholdmetricname* должен иметь значение NULL.  
  
 [ **@value** =] *значение*  
 Новое значение для пороговой метрики публикации. *значение* — **int**, значение по умолчанию NULL. Если **null**, а затем значение метрики не обновляется.  
  
 [ **@shouldalert** =] *shouldalert*  
 Указывает, создается ли предупреждение при достижении пороговой метрики публикации. *shouldalert* — **бит**, значение по умолчанию NULL. Значение **1** означает, что оповещение создается, а значение **0** означает, что оповещение не создается.  
  
 [ **@mode** =] *режим*  
 Определяет, активна ли метрика порогового показателя публикации. *режим* — **tinyint**, значение по умолчанию **1**. Значение **1** означает, что включено наблюдение за данной метрикой, а значение **2** означает, что наблюдение за данной метрикой отключен.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_replmonitorchangepublicationthreshold** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** или **replmonitor** предопределенной роли базы данных в базе данных распространителя могут выполнять процедуру **sp_replmonitorchangepublicationthreshold**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
