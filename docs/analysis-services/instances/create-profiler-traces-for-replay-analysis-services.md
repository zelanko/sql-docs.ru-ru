---
title: Создание трассировок Profiler для воспроизведения (службы Analysis Services) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 36ae9263a6ce5f92e144b34c232dd1c096a6609d
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147339"
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Чтобы воспроизвести запросы, результаты обнаружения и команды, отправляемые пользователями служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно собрать требуемые события. Чтобы инициировать сбор этих событий, должны быть выбраны соответствующие классы событий на вкладке **Выбор событий** диалогового окна **Свойства трассировки** . Например, если выбирается класс событий «Начало запроса», то события, содержащие запросы, собираются и используются для воспроизведения. Также файл трассировки содержит достаточное количество сведений для поддержки воспроизведения серверных транзакций в распределенной среде в оригинальной последовательности транзакций.  
  
## <a name="replay-for-queries"></a>Воспроизведение запросов  
 Чтобы воспроизвести запросы, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Audit Login со всеми его столбцами данных. Этот класс событий предоставляет сведения о каждом пользователе, вошедшем в систему, а также о параметрах сеанса. Серверный идентификатор процесса (SPID) предоставляет ссылку на пользовательский сеанс. Дополнительные сведения см. в статье [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).  
  
-   Класс событий Query Begin со всеми его столбцами данных. Этот класс событий предоставляет сведения о запросе, который был переслан службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Столбец «Подкласс событий» предоставляет сведения о типе запроса. Столбец TextData предоставляет реальный текст запроса. Столбец RequestParameters предоставляет параметры для параметризованных запросов, а столбец RequestProperties — свойства запроса XML для аналитики (XMLA). Дополнительные сведения см. в статье [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).  
  
-   Класс событий Query End со всеми его столбцами данных. Этот класс событий проверяет состояние выполнения запроса. Дополнительные сведения см. в статье [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).  
  
## <a name="replay-for-discovers"></a>Воспроизведение открытий  
 Чтобы воспроизвести открытия, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Audit Login со всеми его столбцами данных. Этот класс событий предоставляет сведения о каждом пользователе, вошедшем в систему, а также о параметрах сеанса. SPID предоставляет ссылку на пользовательский сеанс. Дополнительные сведения см. в статье [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).  
  
-   Класс событий Discover Begin со всеми его столбцами данных. Столбец TextData предоставляет \<RequestType > часть запроса открытия, а столбец RequestProperties предоставляет \<свойства > часть запроса распознавания. Столбец EventSubclass предоставляет тип обнаружения. Дополнительные сведения см. в статье [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).  
  
-   Класс событий Discover End со всеми его столбцами данных. Этот класс событий проверяет состояние запроса открытия. Дополнительные сведения см. в статье [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).  
  
## <a name="replay-for-commands"></a>Воспроизведение команд  
 Чтобы воспроизвести команды, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должно записать следующие события:  
  
-   Класс событий Command Begin со всеми его столбцами данных. Столбец TextData содержит такие сведения о команде, как тип процесса, идентификатор базы данных и идентификатор куба. Столбец RequestParameters предоставляет параметры для параметризованной команды, а столбец RequestProperties — свойства запроса XMLA. Дополнительные сведения см. в статье [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).  
  
-   Класс событий Command End со всеми его столбцами данных. Этот класс событий проверяет состояние команды. Дополнительные сведения см. в статье [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)   
 [Введение в мониторинг служб Analysis Services при помощи приложения SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
