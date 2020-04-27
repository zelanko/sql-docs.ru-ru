---
title: Создать трассировки профилировщика для воспроизведения (Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc494fa63064d5c48c94e44cb91db5b1fe0f988d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080136"
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)
  Чтобы воспроизвести запросы, обнаружения и команды, отправляемые [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]пользователями в, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] необходимо собрать необходимые события. Чтобы инициировать сбор этих событий, должны быть выбраны соответствующие классы событий на вкладке **Выбор событий** диалогового окна **Свойства трассировки** . Например, если выбирается класс событий «Начало запроса», то события, содержащие запросы, собираются и используются для воспроизведения. Также файл трассировки содержит достаточное количество сведений для поддержки воспроизведения серверных транзакций в распределенной среде в оригинальной последовательности транзакций.  
  
## <a name="replay-for-queries"></a>Воспроизведение запросов  
 Чтобы воспроизвести запросы, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Audit Login со всеми его столбцами данных. Этот класс событий предоставляет сведения о каждом пользователе, вошедшем в систему, а также о параметрах сеанса. Серверный идентификатор процесса (SPID) предоставляет ссылку на пользовательский сеанс. Дополнительные сведения см. в статье [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).  
  
-   Класс событий Query Begin со всеми его столбцами данных. Этот класс событий предоставляет сведения о запросе, который был переслан службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Столбец «Подкласс событий» предоставляет сведения о типе запроса. Столбец TextData предоставляет реальный текст запроса. Столбец RequestParameters предоставляет параметры для параметризованных запросов, а столбец RequestProperties — свойства запроса XML для аналитики (XMLA). Дополнительные сведения см. в статье [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).  
  
-   Класс событий Query End со всеми его столбцами данных. Этот класс событий проверяет состояние выполнения запроса. Дополнительные сведения см. в статье [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).  
  
## <a name="replay-for-discovers"></a>Воспроизведение открытий  
 Чтобы воспроизвести открытия, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Audit Login со всеми его столбцами данных. Этот класс событий предоставляет сведения о каждом пользователе, вошедшем в систему, а также о параметрах сеанса. SPID предоставляет ссылку на пользовательский сеанс. Дополнительные сведения см. в статье [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).  
  
-   Класс событий Discover Begin со всеми его столбцами данных. Столбец TextData предоставляет \<часть запроса Discover>, а столбец RequestProperties предоставляет \<свойства> части запроса Discover. Столбец EventSubclass предоставляет тип обнаружения. Дополнительные сведения см. в статье [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).  
  
-   Класс событий Discover End со всеми его столбцами данных. Этот класс событий проверяет состояние запроса открытия. Дополнительные сведения см. в статье [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).  
  
## <a name="replay-for-commands"></a>Воспроизведение команд  
 Чтобы воспроизвести команды, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Command Begin со всеми его столбцами данных. Столбец TextData содержит такие сведения о команде, как тип процесса, идентификатор базы данных и идентификатор куба. Столбец RequestParameters предоставляет параметры для параметризованной команды, а столбец RequestProperties — свойства запроса XMLA. Дополнительные сведения см. в статье [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).  
  
-   Класс событий Command End со всеми его столбцами данных. Этот класс событий проверяет состояние команды. Дополнительные сведения см. в статье [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).  
  
## <a name="see-also"></a>См. также  
 [События трассировки Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)   
 [Введение в мониторинг служб Analysis Services при помощи приложения SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
