---
title: sp_dbmmonitorhelpalert (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorhelpalert_TSQL
- sp_dbmmonitorhelpalert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorhelpalert
- database mirroring [SQL Server], monitoring
ms.assetid: 43911660-b4e4-4934-8c02-35221160aaec
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0718f99372e0850f1d4b9482236e8750129b8906
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdbmmonitorhelpalert-transact-sql"></a>sp_dbmmonitorhelpalert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о порогах предупреждения для одной или всех ключевых метрик производительности монитора зеркального отображения базы данных.  
 
  ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitorhelpalert database_name   
    [ , alert_id ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Указывает базу данных.  
  
 [ *alert_id* ]  
 Целочисленное значение, идентифицирующее возвращаемое предупреждение. Если этот аргумент не указан, возвращаются все предупреждения, но не срок хранения.  
  
 Для возврата конкретного предупреждения следует указать одно из следующих значений:  
  
|Значение|Метрика производительности|Пороговое значение предупреждения|  
|-----------|------------------------|-----------------------|  
|1|Самая старая неотправленная транзакция|Указывает количество транзакций за минуту, которые могут накопиться в очереди передачи перед тем, как будет сформировано предупреждение в экземпляре основного сервера. Это предупреждение помогает измерять возможную потерю данных за период времени. Это особенно уместно в режиме высокой производительности. Однако это предупреждение также уместно в режиме высокой безопасности, когда зеркальное отображение приостановлено или прекращено, потому что участники были разъединены.|  
|2|Неотправленный журнал|Указывает, какое количество килобайтов (КБ) неотправленного журнала формирует предупреждение в экземпляре основного сервера. Это предупреждение помогает измерять возможную потерю данных в КБ. Это особенно уместно в режиме высокой производительности. Однако это предупреждение также уместно в режиме высокой безопасности, когда зеркальное отображение приостановлено или прекращено, потому что участники были разъединены.|  
|3|Невосстановленный журнал|Указывает, какое количество килобайтов (КБ) невосстановленного журнала формирует предупреждение в экземпляре зеркального сервера. Это предупреждение помогает вычислить время отработки отказа. *Время отработки отказа* в основном состоит из времени, необходимого бывшему зеркальному серверу для наката всех журналов, оставшихся в его очереди повторов, и небольшого дополнительного времени.|  
|4|Затраты на фиксирование изменений на зеркальном сервере|Указывает количество миллисекунд средней задержки транзакции, которая допустима перед формированием предупреждения на основном сервере. Задержка — это объем дополнительной нагрузки во время ожидания экземпляром основного сервера экземпляра зеркального сервера для добавления записи журнала транзакции в очередь повтора. Это значение уместно только в режиме высокой безопасности.|  
|5|Срок хранения|Метаданные, управляющие длительностью хранения строк в таблице состояния зеркального отображения базы данных.|  
  
 Сведения об идентификаторах событий, соответствующих предупреждениям см. в разделе [пороговых значений предупреждений и оповещений в метриках производительности зеркального отображения &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 Для каждого возвращаемого предупреждения возвращает строку, содержащую следующие столбцы:  
  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|**alert_id**|**int**|В таблице ниже перечислены **alert_id** значение для каждой метрики производительности и единицы измерения метрики, отображаемые в **sp_dbmmonitorresults** результирующего набора:|  
|**Пороговое значение**|**int**|Пороговое значение для предупреждения. Если при обновлении состояния зеркального отображения возвращено значение выше данного порога, в журнал событий Windows будет внесена запись. Это значение измеряется в килобайтах, минутах или миллисекундах, в зависимости от типа предупреждения. Если порог в данный момент не установлен, значение принимается равным NULL.<br /><br /> **Примечание:** для просмотра текущих значений, запустите [sp_dbmmonitorresults](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md) хранимой процедуры.|  
|**Включен**|**бит**|0 = событие отключено.<br /><br /> 1 = событие включено.<br /><br /> **Примечание:** срок хранения всегда включен.|  
  
|Значение|Метрика производительности|Единицы|  
|-----------|------------------------|----------|  
|1|Самая старая неотправленная транзакция|Минуты|  
|2|Неотправленный журнал|КБ|  
|3|Невосстановленный журнал|КБ|  
|4|Затраты на фиксирование изменений на зеркальном сервере|Миллисекунды|  
|5|Срок хранения|Часы|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает строку, указывающую на то, включено ли предупреждение для метрики производительности наиболее старой неотправленной транзакции в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_dbmmonitorhelpalert AdventureWorks2012, 1 ;  
```  
  
 Следующий пример возвращает строку для каждой метрики производительности, указывающую на то, включена ли она в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_dbmmonitorhelpalert AdventureWorks2012;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorupdate &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
