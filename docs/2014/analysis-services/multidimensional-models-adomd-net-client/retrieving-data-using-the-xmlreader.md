---
title: Получение данных с помощью XmlReader | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- retrieving data
- XmlReader object
- data retrieval [ADOMD.NET], XmlReader object
ms.assetid: 420ec40e-be2d-413a-b4b2-6d2b1756e270
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: caa8ef058839fb3c97a9e3dfdf6022dd91bc2053
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165694"
---
# <a name="retrieving-data-using-the-xmlreader"></a>Получение данных с помощью объекта XmlReader
  `XmlReader` Класса часть `System.Xml` пространство имен для библиотеки классов Microsoft .NET Framework аналогичен <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> класс, в который `XmlReader` класс также предоставляет быстрый некэшируемый однопроходный доступ к данным. Если нет необходимости создавать аналитическое представление данных в памяти с помощью объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, то для получения XML-данных (особенно больших объемов) хорошо подходит объект `XmlReader`. Так как `XmlReader` выполняет потоковую передачу данных, `XmlReader` нет необходимости получать и кэшировать все данные перед передачей их вызывающему объекту, как если бы в том случае, если <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> объекта были использованы для преобразования ответа XML для аналитики в аналитические объекта представление модели.  
  
 Класс `XmlReader` обеспечивает прямой доступ к ответу XML для аналитики, полученному ADOMD.NET, через вызов метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Синтаксический анализ полученных данных необходимо выполнить вручную, поскольку они представляют собой необработанный XML. Объект `XmlReader` должен быть закрыт сразу же после получения данных.  
  
## <a name="retrieving-data-and-metadata"></a>Получение данных и метаданных  
 Чтобы произвести получение данных с помощью класса `XmlReader`, выполните следующие шаги.  
  
1.  **Создайте новый экземпляр объекта.**  
  
     Для создания нового экземпляра класса `XmlReader` вызывается метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Получение данных.**  
  
     После того как команда выполнит запрос и вернет объект `XmlReader`, необходимо произвести синтаксический анализ данных и метаданных. Данные и метаданные XML представлены в собственном формате, используемом поставщиком XML для аналитики. Для большинства поставщиков XML для аналитики собственным является `MDDataSet`. Формат `MDDataSet` предоставляет данные и метаданные наборов ячеек в хорошо структурированной форме. Дополнительные сведения о формате `MDDataSet` см. в спецификации XML для аналитики.  
  
3.  **Закройте средство чтения.**  
  
     Необходимо вызывать метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> после завершения работы с объектом `XmlReader`. Хотя `XmlReader` открыт, в который `XmlReader` эксклюзивное использование <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> объект, который был использован для выполнения команды. Пока не будет закрыт исходный объект `XmlReader`, выполнение каких-либо команд при помощи этого объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> (включая создание другого объекта `XmlReader` или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>) будет невозможным.  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>Пример получения данных из объекта XmlReader  
 В следующем примере выполняется команда и производится получение данных в виде объекта `XmlReader` с выводом содержимого файла на консоль.  
  
 [!code-csharp[Adomd.NetClient#OutputDataWithXML](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#outputdatawithxml)]  
  
## <a name="see-also"></a>См. также  
 [Получение данных из источника аналитических данных](retrieving-data-from-an-analytical-data-source.md)   
 [Получение данных с помощью объекта CellSet](retrieving-data-using-the-cellset.md)   
 [Получение данных с помощью объекта AdomdDataReader](retrieving-data-using-the-adomddatareader.md)  
  
  
