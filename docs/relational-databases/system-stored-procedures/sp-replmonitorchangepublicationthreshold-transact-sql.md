---
title: sp_replmonitorchangepublicationthreshold (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0bb8c060963f92ec14d140cf3b8649216fd89bf8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850582"
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
 [ **@publisher** =] **"***издателя***"**  
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
 Идентификатор публикации, изменяемой пороговый показатель. *metric_id* — **int**, со значением по умолчанию NULL и может принимать одно из следующих значений.  
  
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
 Имя изменяемого порогового показателя публикации. *thresholdmetricname* — **sysname**, со значением по умолчанию NULL. Необходимо указать либо *thresholdmetricname* или *metric_id*. Если *metric_id* указан, то *thresholdmetricname* должен иметь значение NULL.  
  
 [ **@value** =] *значение*  
 Новое значение для пороговой метрики публикации. *значение* — **int**, со значением по умолчанию NULL. Если **null**, а затем значение метрики не обновляется.  
  
 [ **@shouldalert** =] *shouldalert*  
 Указывает, создается ли предупреждение при достижении пороговой метрики публикации. *shouldalert* — **бит**, значение по умолчанию NULL. Значение **1** означает, что предупреждение создается и значение **0** означает, что предупреждение не создается.  
  
 [ **@mode** =] *режим*  
 Определяет, активна ли метрика порогового показателя публикации. *режим* — **tinyint**, значение по умолчанию **1**. Значение **1** означает, что включено наблюдение за данной метрикой и значением **2** означает, что наблюдение за данной метрикой отключен.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_replmonitorchangepublicationthreshold** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** или **replmonitor** предопределенной роли базы данных в базе данных распространителя могут выполнять процедуру **sp_replmonitorchangepublicationthreshold**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
