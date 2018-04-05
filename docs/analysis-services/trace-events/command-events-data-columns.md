---
title: Команда Events Data Columns | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7f3c3be311e1f0ce7b53bd35b90fb94dfc03f07b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="command-events-data-columns"></a>Столбцы данных командных событий
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В следующей таблице перечислены столбцы данных для каждого класса событий в **командные события** категории событий.  
  
 Категория событий **Командные события** имеет следующие классы событий:  
  
-   [Класс начала команды](#bkmk_1)  
  
-   [Класс конца команды](#bkmk_2)  
  
 В следующих таблицах перечисляются столбцы данных для каждого из этих классов событий.  
  
##  <a name="bkmk_1"></a> Класс начала команды — столбцы данных  
  
|Столбец данных|Description|  
|-----------------|-----------------|  
|ConnectionID|Содержит уникальный идентификатор соединения, связанный с командным событием.|  
|TextData|Содержит текстовые данные, связанные с командным событием.|  
|ServerName|Содержит имя экземпляра служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , где произошло командное событие.|  
|CurrentTime|Содержит текущее время командного события.|  
|DatabaseName|Содержит имя базы данных, в которой выполняется команда.|  
|EventSubclass|Содержит класс события в командном событии. Поддерживаются значения:<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Other|  
|NTUserName|Содержит имя пользователя Windows, связанное с командным событием. Имя пользователя указано в канонической форме. Например, engineering.microsoft.com/software/user.|  
|RequestProperties|Содержит свойства XML для аналитики запросов (XMLA), связанные с командным событием.|  
|SPID|Содержит идентификатор серверного процесса (SPID), уникальным образом определяющий сеанс пользователя, который связан с командным событием. Идентификатор SPID напрямую соответствует идентификатору GUID сеанса, используемому XML для аналитики.|  
|StartTime|Содержит время начала командного события (при наличии).|  
|SessionType|Содержит сущность, которая вызвала операцию.|  
|NTDomainName|Содержит учетную запись домена Windows, связанную с событием разрешения объекта.|  
|ClientProcessID|Содержит уникальный идентификатор клиентского процесса, связанный с командным событием.|  
  
##  <a name="bkmk_2"></a> Класс конца команды — столбцы данных  
  
|Столбец данных|Description|  
|-----------------|-----------------|  
|ConnectionID|Содержит уникальный идентификатор соединения, связанный с командным событием.|  
|TextData|Содержит текстовые данные, связанные с командным событием.|  
|ServerName|Содержит имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , где произошло командное событие.|  
|CurrentTime|Содержит текущее время командного события. Для фильтрации используйте форматы *ГГГГ*-*ММ*-*ДД* и *ГГГГ*-*ММ*-*ДД HH*:*ММ*:*СС*.|  
|DatabaseName|Содержит имя базы данных, в которой выполняется команда.|  
|Duration|Содержит приблизительный интервал времени между началом команды и событием конца команды.|  
|EndTime|Содержит время окончания командного события. Для фильтрации используйте форматы *ГГГГ*-*ММ*-*ДД* и *ГГГГ*-*ММ*-*ДД HH*:*ММ*:*СС*.|  
|EventSubclass|Содержит класс события в командном событии. Поддерживаются значения:<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Other|  
|NTCanonicalUserName|Содержит имя пользователя Windows, связанное с командным событием. Имя пользователя указано в канонической форме. Например, engineering.microsoft.com/software/user.|  
|NTUserName|Содержит учетную запись пользователя Windows, связанную с командным событием.|  
|SPID|Содержит идентификатор серверного процесса (SPID), уникальным образом определяющий сеанс пользователя, который связан с командным событием. Идентификатор SPID напрямую соответствует идентификатору GUID сеанса, используемому XML для аналитики.|  
|StartTime|Содержит время начала события конца команды (при наличии).|  
|CPUTime|Указывает количество времени процессора (в миллисекундах), использованное процессом в интервале между событием начала команды и событием конца команды.|  
|Ошибка|Содержит номер любой ошибки, связанной с командным событием.|  
|Severity|Содержит уровень серьезности исключения, связанного с командным событием. Возможны следующие значения.<br /><br /> 0 = успешное завершение<br /><br /> 1 = информационное сообщение<br /><br /> 2 = предупреждение<br /><br /> 3 = ошибка|  
|Успешно|Указывает на успешность или сбой командного события. Возможны следующие значения.<br /><br /> 0 = неуспешное завершение;<br /><br /> 1 = успешное завершение.|  
|SessionType|Содержит сущность, которая вызвала операцию, связанную с событием конца команды.|  
|NTDomainName|Содержит учетную запись домена Windows, связанную с командным событием.|  
|ClientProcessID|Содержит уникальный идентификатор клиентского процесса, связанный с командным событием.|  
  
## <a name="see-also"></a>См. также:  
 [Command Events Event Category](../../analysis-services/trace-events/command-events-event-category.md)  
  
  
