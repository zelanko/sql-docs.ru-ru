---
title: "Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- replaying queries
- replaying discovers
- events [Analysis Services]
- replaying commands
- Profiler [SQL Server Profiler], Analysis Services
- performance [Analysis Services], replays
- traces [Analysis Services]
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c992aa2f5d666b38290b928bf44e6e5680ba701e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)
  Чтобы воспроизвести запросы, результаты обнаружения и команды, отправляемые пользователями служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно собрать требуемые события. Чтобы инициировать сбор этих событий, должны быть выбраны соответствующие классы событий на вкладке **Выбор событий** диалогового окна **Свойства трассировки** . Например, если выбирается класс событий «Начало запроса», то события, содержащие запросы, собираются и используются для воспроизведения. Также файл трассировки содержит достаточное количество сведений для поддержки воспроизведения серверных транзакций в распределенной среде в оригинальной последовательности транзакций.  
  
## <a name="replay-for-queries"></a>Воспроизведение запросов  
 Чтобы воспроизвести запросы, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Audit Login со всеми его столбцами данных. Этот класс событий предоставляет сведения о каждом пользователе, вошедшем в систему, а также о параметрах сеанса. Серверный идентификатор процесса (SPID) предоставляет ссылку на пользовательский сеанс. Дополнительные сведения см. в статье [Security Audit Data Columns](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
-   Класс событий Query Begin со всеми его столбцами данных. Этот класс событий предоставляет сведения о запросе, который был переслан службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Столбец «Подкласс событий» предоставляет сведения о типе запроса. Столбец TextData предоставляет реальный текст запроса. Столбец RequestParameters предоставляет параметры для параметризованных запросов, а столбец RequestProperties — свойства запроса XML для аналитики (XMLA). Дополнительные сведения см. в статье [Queries Events Data Columns](../../analysis-services/trace-events/queries-events-data-columns.md).  
  
-   Класс событий Query End со всеми его столбцами данных. Этот класс событий проверяет состояние выполнения запроса. Дополнительные сведения см. в статье [Queries Events Data Columns](../../analysis-services/trace-events/queries-events-data-columns.md).  
  
## <a name="replay-for-discovers"></a>Воспроизведение открытий  
 Чтобы воспроизвести открытия, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Audit Login со всеми его столбцами данных. Этот класс событий предоставляет сведения о каждом пользователе, вошедшем в систему, а также о параметрах сеанса. SPID предоставляет ссылку на пользовательский сеанс. Дополнительные сведения см. в статье [Security Audit Data Columns](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
-   Класс событий Discover Begin со всеми его столбцами данных. Столбец TextData предоставляет \<RequestType > предоставляет часть запроса распознавания, а столбец RequestProperties \<свойства > часть запроса распознавания. Столбец EventSubclass предоставляет тип обнаружения. Дополнительные сведения см. в статье [Discover Events Data Columns](../../analysis-services/trace-events/discover-events-data-columns.md).  
  
-   Класс событий Discover End со всеми его столбцами данных. Этот класс событий проверяет состояние запроса открытия. Дополнительные сведения см. в статье [Discover Events Data Columns](../../analysis-services/trace-events/discover-events-data-columns.md).  
  
## <a name="replay-for-commands"></a>Воспроизведение команд  
 Чтобы воспроизвести команды, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Command Begin со всеми его столбцами данных. Столбец TextData содержит такие сведения о команде, как тип процесса, идентификатор базы данных и идентификатор куба. Столбец RequestParameters предоставляет параметры для параметризованной команды, а столбец RequestProperties — свойства запроса XMLA. Дополнительные сведения см. в статье [Command Events Data Columns](../../analysis-services/trace-events/command-events-data-columns.md).  
  
-   Класс событий Command End со всеми его столбцами данных. Этот класс событий проверяет состояние команды. Дополнительные сведения см. в статье [Command Events Data Columns](../../analysis-services/trace-events/command-events-data-columns.md).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [Введение в мониторинг служб Analysis Services при помощи приложения SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  

