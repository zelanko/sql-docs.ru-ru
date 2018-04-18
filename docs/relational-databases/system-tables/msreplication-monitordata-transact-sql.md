---
title: MSreplication_monitordata (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSreplication_monitordata_TSQL
- MSreplication_monitordata
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_monitordata system table
ms.assetid: 843d3ffd-a1ef-4fd5-a744-c2252199793e
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa63fd758591cccf3e619a84aaf7d1184fe706bd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="msreplicationmonitordata-transact-sql"></a>MSreplication_monitordata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_monitordata** таблица содержит кэшированные данные, используемые монитором репликации, по одной строке для каждой из отслеживаемых подписок. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**lastrefresh**|**datetime**|Дата и время обновления монитора.|  
|**computetime**|**int**|Время (в секундах), которое заняло вычисление отслеживаемых данных.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_srvid**|**int**|Идентификатор сервера издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**Публикации**|**sysname**|Имя публикации.|  
|**publication_type**|**int**|Тип публикации, может принимать одно из следующих значений:<br /><br /> **0** = публикация транзакций<br /><br /> **1** = публикация моментальных снимков<br /><br /> **2** = публикация слиянием|  
|**agent_type**|**int**|Тип агента репликации, может принимать одно из следующих значений.<br /><br /> **1** = агент моментальных снимков<br /><br /> **2** = агент чтения журнала<br /><br /> **3** = агент распространителя<br /><br /> **4** = агент слияния<br /><br /> **9** = агент чтения очереди|  
|**agent_id**|**int**|Идентификатор агента репликации.|  
|**agent_name**|**sysname**|Имя задания агента репликации.|  
|**job_id**|**uniqueidentifier**|Идентификатор GUID задания агента репликации.|  
|**status**|**int**|Состояние агента репликации, может принимать одно из следующих значений:<br /><br /> **1** = запущен<br /><br /> **2** = выполнено успешно<br /><br /> **3** = выполняется<br /><br /> **4** = бездействует<br /><br /> **5** = Повтор<br /><br /> **6** = ошибка|  
|**isagentrunningnow**|**бит**|Флаг, указывающий, если задание агента выполняется, где значение **1** означает, что задание выполняется.|  
|**Предупреждение**|**int**|Пороговое предупреждение, сформированное подпиской, может быть результатом логической операции OR следующих значений:<br /><br /> **1** = expiration — подписка на публикацию транзакций превысил срок хранения превышает допустимый порог, в процентах от срока хранения.<br /><br /> **2** = latency — превышение времени для репликации данных транзакционного издателя подписчику пороговое значение, указанное в секундах.<br /><br /> **4** = mergeexpiration — подписка на публикацию слиянием превысил срок хранения превышает допустимый порог, в процентах от срока хранения. 8 = mergefastrunduration — время, затраченное на завершение синхронизации подписки слиянием, превысило пороговое значение, указанное в секундах, для быстрого сетевого соединения.<br /><br /> **16** = mergeslowrunduration — время, затраченное на завершение синхронизации подписки слиянием через медленное или коммутируемое сетевое соединение превышает значение, в секундах.<br /><br /> **32** = mergefastrunspeed — скорость доставки строк при синхронизации подписки на публикацию слиянием оказалась пороговой, в строках в секунду, через быстрое сетевое соединение.<br /><br /> **64** = mergefastrunspeed — скорость доставки строк при синхронизации подписки на публикацию слиянием не достигла порогового значения, в строках в секунду, через медленное или коммутируемое сетевое соединение.|  
|**last_distsync**|**datetime**|Дата и время последнего запуска агента распространителя.|  
|**agentstoptime**|**datetime**|Дата и время остановки агента.|  
|**distdb**|**sysname**|Имя базы данных распространителя для данной подписки.|  
|**Хранения**|**int**|Срок хранения для публикации.|  
|**Отметка_времени**|**datetime**|Только для внутреннего использования.|  
|**worst_latency**|**int**|Наибольшая задержка (в секундах) при изменении данных, зафиксированная для публикации транзакций агентом чтения журнала или агентом распространителя.|  
|**best_latency**|**int**|Наименьшая задержка (в секундах) изменения данных, зафиксированная для публикации транзакций агентом чтения журнала или агентом распространителя.|  
|**avg_latency**|**int**|Средняя задержка (в секундах) изменения данных, зафиксированная для публикации транзакций агентом чтения журнала или агентом распространителя.|  
|**cur_latency**|**int**|Задержка (в секундах) при изменении данных, зафиксированная для публикации транзакций агентом чтения журнала или агентом распространителя для текущего запуска.|  
|**worst_runspeedPerf**|**int**|Наибольшая длительность синхронизации для публикации слиянием|  
|**best_runspeedPerf**|**int**|Наименьшая длительность синхронизации для публикации слиянием|  
|**average_runspeedPerf**|**int**|Средняя длительность синхронизации для публикации слиянием|  
|**mergePerformance**|**int**|Производительность последней синхронизации по сравнению со всеми синхронизациями для данной подписки. Вычисляется как скорость доставки последней синхронизации, поделенная на среднее арифметическое скоростей доставки для всех предыдущих синхронизаций.|  
|**mergelatestsessionrunduration**|**int**|Длительность самого последнего выполнения агента слияния.|  
|**mergelatestsessionrunspeed**|**float(53)**|Скорость доставки при самом последнем выполнении агента слияния.|  
|**mergelatestsessionconnectiontype**|**int**|Тип соединения, использованный последним сеансом агента слияния, может принимать одно из следующих значений:<br /><br /> **1** = локальная сеть (LAN)<br /><br /> **2** = коммутируемое сетевое соединение|  
|**retention_period_unit**|**tinyint**|Определяет единицу измерения для указания срока хранения, может принимать одно из следующих значений:<br /><br /> **1** = Неделя<br /><br /> **2** = Месяц<br /><br /> **3** = Год|  
  
## <a name="see-also"></a>См. также  
 [Наблюдать за репликацией программно](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replmonitorhelpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md)   
 [sp_replmonitorhelppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md)   
 [sp_replmonitorhelppublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md)   
 [sp_replmonitorhelpmergesession &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md)   
 [sp_replmonitorhelppublicationthresholds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md)   
 [sp_replmonitorhelpmergesessiondetail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md)  
  
  
