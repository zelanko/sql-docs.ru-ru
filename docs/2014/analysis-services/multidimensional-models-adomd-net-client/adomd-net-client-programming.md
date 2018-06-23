---
title: Программирование клиента ADOMD.NET | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 55156115-ecd1-4ed9-876e-23406af9bbf9
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9faa64cce77c883ed6adb86bca6d50f32f015c97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192774"
---
# <a name="adomdnet-client-programming"></a>Программирование клиента ADOMD.NET
  Клиентские компоненты ADOMD.NET находятся в пространстве имен `Microsoft.AnalysisServices.AdomdClient` (файл microsoft.analysisservices.adomdclient.dll). Клиентские компоненты обеспечивают функциональные возможности для клиента и приложений среднего уровня возможность запрашивать данные и метаданные из хранилища аналитических данных, таких как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="using-the-adomdnet-client-objects"></a>Использование клиентских объектов ADOMD.NET  
 Существует набор наиболее типичных действий при выполнении запроса к источнику аналитических данных. В следующей таблице приведены наиболее часто используемые задачи, в которых клиентские объекты ADOMD.NET используются для выполнения такого запроса.  
  
|Задача|Описание|  
|----------|-----------------|  
|[Установление соединений в ADOMD.NET](connections-in-adomd-net.md)|Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> используется в ADOMD.NET для установления соединений с источниками аналитических данных, например базами данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> может применяться для выполнения команд, получения данных и метаданных из источника аналитических данных.|  
|[Получение метаданных из источника аналитических данных](retrieving-metadata-from-an-analytical-data-source.md)|Получить сведения о базовом источнике данных можно после установления соединения при помощи широкого спектра объектов. Это позволяет приложению адаптироваться к источнику данных, с которым оно соединено.|  
|[Выполнение команд в источнике аналитических данных](executing-commands-against-an-analytical-data-source.md)|Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> обеспечивает интерфейсы, необходимые для выполнения команд в базовом источнике аналитических данных.|  
|[Получение данных из источника аналитических данных](retrieving-data-from-an-analytical-data-source.md)|После выполнения команды данные можно получить и выполнить их синтаксический анализ при помощи объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> или `System.XmlReader`.|  
|[Выполнение транзакций в ADOMD.NET](../../relational-databases/native-client-ole-db-transactions/transactions.md)|Все действия, перечисленные в предыдущих строках этой таблицы, могут производиться в рамках транзакции READ-COMMITTED, в которой во время чтения данных устанавливаются совмещаемые блокировки для предотвращения чтения «грязных» данных. Данные по-прежнему можно изменять до окончания транзакции, что вызывает чтение без возможности повторения или фантомные данные. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> обеспечивает поддержку транзакций в ADOMD.NET.|  
  
 Взаимодействие с иерархией объектов ADOMD.NET обычно начинается с одного или нескольких объектов верхнего уровня, как описано в следующей таблице.  
  
|Чтобы|Используемый объект|  
|--------|---------------------|  
|Соединение с источником аналитических данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> представляет и соединение с источником данных, и метаданные этого источника. Например, можно подключиться к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] локального куба (cub) файла, а затем <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> , чтобы получить метаданные о кубах, имеющихся в источнике аналитических данных. Кроме того, этот объект представляет реализацию интерфейса `IDbConnection`, который необходим всем поставщикам данных платформы .NET Framework.|  
|Возможности источника данных по интеллектуальному анализу|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> содержит несколько коллекций интеллектуального анализа данных.<br /><br /> - <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> Содержит список всех моделей интеллектуального анализа данных в источнике данных.<br />- <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> Предоставляет сведения об алгоритмах интеллектуального анализа данных.<br />- <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> Предоставляет информацию о структурах интеллектуального анализа данных на сервере.|  
|Выполнение запросов к источнику данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> представляет инструкцию или запрос, который будет отправлен на сервер. После установления соединения с источником данных объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> используется для выполнения инструкций на поддерживаемом языке, например языке MDX или DMX. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> также может быть использован для возврата результатов из объектов <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> и <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.|  
|Быстрое и эффективное получение данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> можно создать с помощью вызова метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Этот объект реализует интерфейс `IDbDataReader` из пространства имен `System.Data` библиотеки классов платформы .NET Framework.|  
|Получение аналитических данных с наибольшим объемом метаданных|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> можно создать вызовом метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. После того как объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> вернул объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, можно просмотреть аналитические данные, содержащиеся в объекте <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>.|  
|Получение метаданных о кубах (доступных измерений, мер, именованных наборов и др.)|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> представляет метаданные о кубе. Объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> доступен по ссылке из объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
|Получение данных с помощью интерфейса `System.Data.IDbDataAdapter`|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter> обеспечивает поддержку режима «только для чтения» для существующих клиентских приложений платформы .NET Framework.|  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [Разработка с использованием ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  