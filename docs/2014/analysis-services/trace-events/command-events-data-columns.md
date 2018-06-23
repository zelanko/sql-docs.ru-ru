---
title: Команда Events Data Columns | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 290c9ca23a71c43d16f29e0bd0e6d1f595b6df14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086975"
---
# <a name="command-events-data-columns"></a>Столбцы данных командных событий
  В следующей таблице перечислены столбцы данных для данного класса событий в категории событий **Командные события** .  
  
 Категория событий **Командные события** имеет следующие классы событий:  
  
-   [Класс начала команды](#bkmk_1)  
  
-   [Класс конца команды](#bkmk_2)  
  
 В следующих таблицах перечисляются столбцы данных для каждого из этих классов событий.  
  
##  <a name="bkmk_1"></a> Класс начала команды — столбцы данных  
  
|Столбец данных|Описание|  
|-----------------|-----------------|  
|ConnectionID|Содержит уникальный идентификатор соединения, связанный с командным событием.|  
|TextData|Содержит текстовые данные, связанные с командным событием.|  
|ServerName|Содержит имя экземпляра служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , где произошло командное событие.|  
|CurrentTime|Содержит текущее время командного события.|  
|DatabaseName|Содержит имя базы данных, в которой выполняется команда.|  
|EventSubclass|Содержит класс события в командном событии. Возможны следующие значения.<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Other|  
|NTUserName|Содержит имя пользователя Windows, связанное с командным событием. Имя пользователя указано в канонической форме. Например, engineering.microsoft.com/software/user.|  
|RequestProperties|Содержит свойства XML для аналитики запросов (XMLA), связанные с командным событием.|  
|SPID|Содержит идентификатор серверного процесса (SPID), уникальным образом определяющий сеанс пользователя, который связан с командным событием. Идентификатор SPID напрямую соответствует идентификатору GUID сеанса, используемому XML для аналитики.|  
|StartTime|Содержит время начала командного события (при наличии).|  
|SessionType|Содержит сущность, которая вызвала операцию.|  
|NTDomainName|Содержит учетную запись домена Windows, связанную с событием разрешения объекта.|  
|ClientProcessID|Содержит уникальный идентификатор клиентского процесса, связанный с командным событием.|  
  
##  <a name="bkmk_2"></a> Класс конца команды — столбцы данных  
  
|Столбец данных|Описание|  
|-----------------|-----------------|  
|ConnectionID|Содержит уникальный идентификатор соединения, связанный с командным событием.|  
|TextData|Содержит текстовые данные, связанные с командным событием.|  
|ServerName|Содержит имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , где произошло командное событие.|  
|CurrentTime|Содержит текущее время командного события. Для фильтрации используйте форматы *ГГГГ*-*ММ*-*ДД* и *ГГГГ*-*ММ*-*ДД HH*:*ММ*:*СС*.|  
|DatabaseName|Содержит имя базы данных, в которой выполняется команда.|  
|Duration|Содержит приблизительный интервал времени между началом команды и событием конца команды.|  
|EndTime|Содержит время окончания командного события. Для фильтрации используйте форматы *ГГГГ*-*ММ*-*ДД* и *ГГГГ*-*ММ*-*ДД HH*:*ММ*:*СС*.|  
|EventSubclass|Содержит класс события в командном событии. Возможны следующие значения.<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Other|  
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
  
## <a name="see-also"></a>См. также  
 [Категория событий «Командные события»](command-events-event-category.md)  
  
  