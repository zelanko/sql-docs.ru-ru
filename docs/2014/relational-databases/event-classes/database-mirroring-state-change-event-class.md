---
title: Класс событий Database Mirroring State Change | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- database mirroring [SQL Server], event notifications
- Database Mirroring State Change event class
ms.assetid: f936a99e-2a81-4768-8177-5c969bbe2e04
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f81b196ee1b686fbe2dd3563f694411a0e00d962
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62663048"
---
# <a name="database-mirroring-state-change-event-class"></a>Database Mirroring State Change, класс событий
  Класс событий **Database Mirroring State Change** указывает на изменение состояния зеркальной базы данных. Он включается в трассировки, выполняющие мониторинг состояния зеркальных баз данных.  
  
 Если класс событий **Database Mirroring State Change** включен в трассировку, связанные с этим издержки невелики, но они могут возрасти, если зеркальная база данных находится в состоянии повышенной нагрузки.  
  
## <a name="data-database-mirroring-state-change-event-class-data-columns"></a>Столбцы данных класса событий Database Mirroring State Change  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя зеркальной базы данных.|35|Да|  
|**EventClass**|**int**|Тип события = 167.|27|Нет|  
|**EventSequence**|**int**|Порядковый номер класса событий в пакете.|51|Нет|  
|**IntegerData**|**int**|Идентификатор предыдущего состояния.|25|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого выполняется трассировка.|26|Нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени Имя_входа1 и при выполнении инструкции под именем Имя_входа2 **SessionLoginName** содержит значение «Имя_входа1», а **LoginName** содержит значение «Имя_входа2». В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Состояние**|**int**|Идентификатор нового состояния зеркального отображения:<br /><br /> 0 = нулевое уведомление<br /><br /> 1 = синхронизированная основная база данных со следящим сервером<br /><br /> 2 = синхронизированная основная база данных без следящего сервера<br /><br /> 3 = синхронизированная зеркальная база данных со следящим сервером<br /><br /> 4 = синхронизированная зеркальная база данных без следящего сервера<br /><br /> 5 = связь с основной базой данных потеряна<br /><br /> 6 = связь с зеркальной базой данных потеряна<br /><br /> 7 = отработка отказа вручную<br /><br /> 8 = автоматическая отработка отказа<br /><br /> 9 = зеркальное отображение приостановлено<br /><br /> 10 = нет кворума<br /><br /> 11 = синхронизация зеркальной базы данных<br /><br /> 12 = основная база данных работает без зеркального отображения|30|Да|  
|**TextData**|**ntext**|Описание изменения состояния.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
