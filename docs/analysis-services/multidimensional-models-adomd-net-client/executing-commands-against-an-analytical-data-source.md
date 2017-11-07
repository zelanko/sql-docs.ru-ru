---
title: "Выполнение команд в источнике аналитических данных | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: fb114c28985fa0891b7b174c146b1a50730c7866
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="executing-commands-against-an-analytical-data-source"></a>Выполнение команд в источнике аналитических данных
  После установления соединения с источником аналитических данных объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> позволяет выполнять команды в этом источнике данных и возвращать из него результаты. Эти команды могут получать данные при использовании многомерных выражений, расширений интеллектуального анализа данных или даже ограниченного синтаксиса языка SQL. Кроме того, команды языка ASSL позволяют изменять данные в базе данных.  
  
## <a name="creating-a-command"></a>Создание команды  
 Перед выполнением команды ее необходимо создать. Создать команду можно одним из двух способов.  
  
-   Первый способ предусматривает использование конструктора <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, который принимает команду для выполнения в источнике данных, а также объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, в котором команда будет выполняться.  
  
-   Во втором способе используется метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Запрос и изменение текста выполняемой команды производится при помощи свойства <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. Создаваемые команды не обязательно должны возвращать данные после выполнения.  
  
## <a name="running-a-command"></a>Выполнение команды  
 После создания объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> команда предоставляет доступ к нескольким методам <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> для выполнения различных действий. Некоторые из них приведены в следующей таблице.  
  
|Чтобы|Используемый метод|  
|--------|---------------------|  
|Возвращать результаты в виде потока данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A>, возвращает объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Возвращать объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Выполнять команды, которые не возвращают строки|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Вернуть **XMLReader** объект, содержащий данные в формате XML для аналитики (XMLA) совместимый формат|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Пример выполнения команды  
 В этом примере используется <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> для выполнения команды XML для Аналитики, который будет обрабатывать **Adventure Works DW** куба на локальном сервере без возврата данных.  
  
 [!code-cs[Adomd.NetClient#ExecuteXMLAProcessCommand](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/executing-commands-again_1.cs)]  
  
  

