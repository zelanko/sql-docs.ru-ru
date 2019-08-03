---
title: sp_replmonitorchangepublicationthreshold (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7fd8dd31b1468cb718af286f6c00e26cfa2e1ba0
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771220"
---
# <a name="spreplmonitorchangepublicationthreshold-transact-sql"></a>sp_replmonitorchangepublicationthreshold (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя опубликованной базы данных. *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации, для которой изменяются пороговые атрибуты мониторинга. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication_type = ] publication_type`Тип публикации. *publication_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Публикация транзакций.|  
|**1**|Публикация моментальных снимков.|  
|**2**|Публикация слиянием.|  
|NULL (по умолчанию)|Репликация пытается определить тип публикации.|  
  
`[ @metric_id = ] metric_id`Идентификатор изменяемой пороговой метрики публикации. *METRIC_ID* имеет **тип int**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Имя метрики|  
|-----------|-----------------|  
|**1**|**expiration** следит за приближающимся истечением срока подписки на публикации транзакций.|  
|**2**|**latency** следит за производительностью подписки на публикации транзакций.|  
|**4**|**mergeexpiration** следит за приближающимся истечением срока подписки на публикации слиянием.|  
|**5**|**mergeslowrunduration** — отслеживает продолжительность синхронизации слиянием через подключения с низкой пропускной способностью (коммутируемое подключение).|  
|**6**|**mergefastrunduration** — отслеживает продолжительность синхронизации слиянием через подключения локальной сети с высокой пропускной способностью.|  
|**7**|**mergefastrunspeed** — следит за частотой синхронизаций слиянием через соединения с высокой пропускной способностью (локальная сеть).|  
|**8**|**mergefastrunspeed** — следит за частотой синхронизации слиянием через подключения с низкой пропускной способностью (коммутируемое подключение).|  
  
 Необходимо указать либо *METRIC_ID* , либо *срешолдметрикнаме*. Если указан *срешолдметрикнаме* , то *METRIC_ID* должен иметь значение null.  
  
`[ @thresholdmetricname = ] 'thresholdmetricname'`Имя изменяемой пороговой метрики публикации. *срешолдметрикнаме* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *срешолдметрикнаме* , либо *METRIC_ID*. Если указан *METRIC_ID* , то *срешолдметрикнаме* должен иметь значение null.  
  
`[ @value = ] value`Новое значение пороговой метрики публикации. *значение* равно **int**и значение по умолчанию NULL. При значении **null**значение метрики не обновляется.  
  
`[ @shouldalert = ] shouldalert`Имеет значение, если предупреждение создается при достижении пороговой метрики публикации. *shouldalert* имеет **бит**и значение по умолчанию NULL. Значение **1** означает, что создается предупреждение, а значение **0** означает, что предупреждение не создается.  
  
`[ @mode = ] mode`Имеет значение, если пороговая метрика публикации включена. *mode* имеет тип **tinyint**и значение по умолчанию **1**. Значение **1** означает, что мониторинг этой метрики включен, а значение **2** означает, что наблюдение за этой метрикой отключено.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_replmonitorchangepublicationthreshold** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли базы данных **db_owner** или **replmonitor** в базе данных распространителя могут выполнять **sp_replmonitorchangepublicationthreshold**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
