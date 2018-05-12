---
title: Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d5928325ffe5b0b98da2058529b1cbb036a445be
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

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
 [Введение в мониторинг служб Analysis Services в SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
