---
title: Программирование клиента ADOMD.NET | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fbef1da93d4edd44cedbf89ef52133a22b5bb6d9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34020231"
---
# <a name="adomdnet-client-programming"></a>Программирование клиента ADOMD.NET
  Клиентские компоненты ADOMD.NET находятся в пределах **Microsoft.AnalysisServices.AdomdClient** пространства имен (в файл microsoft.analysisservices.adomdclient.dll). Клиентские компоненты обеспечивают функциональные возможности для клиента и приложений среднего уровня возможность запрашивать данные и метаданные из хранилища аналитических данных, таких как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="using-the-adomdnet-client-objects"></a>Использование клиентских объектов ADOMD.NET  
 Существует набор наиболее типичных действий при выполнении запроса к источнику аналитических данных. В следующей таблице приведены наиболее часто используемые задачи, в которых клиентские объекты ADOMD.NET используются для выполнения такого запроса.  
  
|Задача|Описание|  
|----------|-----------------|  
|[Установление соединений в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)|Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> используется в ADOMD.NET для установления соединений с источниками аналитических данных, например базами данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> может применяться для выполнения команд, получения данных и метаданных из источника аналитических данных.|  
|[Получение метаданных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)|Получить сведения о базовом источнике данных можно после установления соединения при помощи широкого спектра объектов. Это позволяет приложению адаптироваться к источнику данных, с которым оно соединено.|  
|[Выполнение команд в источнике аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)|Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> обеспечивает интерфейсы, необходимые для выполнения команд в базовом источнике аналитических данных.|  
|[Получение данных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)|После выполнения команды может быть получен и проанализированные данные в помощью <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, или **System.XmlReader** объектов.|  
|[Выполнение транзакций в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-performing-transactions.md)|Все действия, перечисленные в предыдущих строках этой таблицы, могут производиться в рамках транзакции READ-COMMITTED, в которой во время чтения данных устанавливаются совмещаемые блокировки для предотвращения чтения «грязных» данных. Данные по-прежнему можно изменять до окончания транзакции, что вызывает чтение без возможности повторения или фантомные данные. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> обеспечивает поддержку транзакций в ADOMD.NET.|  
  
 Взаимодействие с иерархией объектов ADOMD.NET обычно начинается с одного или нескольких объектов верхнего уровня, как описано в следующей таблице.  
  
|Чтобы|Используемый объект|  
|--------|---------------------|  
|Соединение с источником аналитических данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> представляет и соединение с источником данных, и метаданные этого источника. Например, можно подключиться к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] локального куба (cub) файла, а затем <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> , чтобы получить метаданные о кубах, имеющихся в источнике аналитических данных. Этот объект также представляет реализацию **IDbConnection** интерфейс, который требуется для всех поставщиков данных .NET Framework.|  
|Возможности источника данных по интеллектуальному анализу|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> содержит несколько коллекций интеллектуального анализа данных.<br /><br /><br /><br /> Коллекция <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> содержит список всех моделей интеллектуального анализа данных в источнике данных.<br /><br /><br /><br /> Коллекция <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> содержит сведения о доступных алгоритмах интеллектуального анализа данных.<br /><br /><br /><br /> Коллекция <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> предоставляет доступ к сведениям о структурах интеллектуального анализа данных на сервере.|  
|Выполнение запросов к источнику данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> представляет инструкцию или запрос, который будет отправлен на сервер. После установления соединения с источником данных объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> используется для выполнения инструкций на поддерживаемом языке, например языке MDX или DMX. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> также может быть использован для возврата результатов из объектов <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> и <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.|  
|Быстрое и эффективное получение данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> можно создать с помощью вызова метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Этот объект реализует **IDbDataReader** интерфейс из **System.Data** имен библиотеки классов .NET Framework.|  
|Получение аналитических данных с наибольшим объемом метаданных|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> можно создать вызовом метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. После того как объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> вернул объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, можно просмотреть аналитические данные, содержащиеся в объекте <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>.|  
|Получение метаданных о кубах (доступных измерений, мер, именованных наборов и др.)|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> представляет метаданные о кубе. Объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> доступен по ссылке из объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
|Получение данных с помощью **System.Data.IDbDataAdapter** интерфейса|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter> обеспечивает поддержку режима «только для чтения» для существующих клиентских приложений платформы .NET Framework.|  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [Разработка с использованием ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  
