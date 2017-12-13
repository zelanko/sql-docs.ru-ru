---
title: "Получение данных с помощью XmlReader | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- retrieving data
- XmlReader object
- data retrieval [ADOMD.NET], XmlReader object
ms.assetid: 420ec40e-be2d-413a-b4b2-6d2b1756e270
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dbcce4f4a75d2aa8aefedfff4c3b8b8de81d1fe6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="retrieving-data-using-the-xmlreader"></a>Получение данных с помощью объекта XmlReader
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]**XmlReader** класса часть **System.Xml** пространство имен для библиотеки классов Microsoft .NET Framework аналогично <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> класса в том, что **XmlReader**класс также предоставляет быстрый некэшируемый однопроходный доступ к данным. Если нет необходимости для представления в памяти и аналитических данных с помощью <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> объекта, **XmlReader** объекта идеально подходит для получения XML-данных, особенно для больших объемов данных. Поскольку **XmlReader** потоки данных, **XmlReader** не должен получать и кэшировать все данные перед передачей вызывающему объекту, как было бы в том случае, если <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> объекта были использованы для преобразования Ответ XML для аналитики в аналитическое представление модели объектов.  
  
 **XmlReader** класс предоставляет прямой доступ к XML-ответа полученных ADOMD.NET при <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> вызывается. Синтаксический анализ полученных данных необходимо выполнить вручную, поскольку они представляют собой необработанный XML. Как можно скорее после получения данных **XmlReader** должен быть закрыт.  
  
## <a name="retrieving-data-and-metadata"></a>Получение данных и метаданных  
 Для использования **XmlReader** класса для получения данных, выполните следующие действия:  
  
1.  **Создайте новый экземпляр объекта.**  
  
     Чтобы создать новый экземпляр **XmlReader** вызвать класс, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> объекта.  
  
2.  **Получение данных.**  
  
     После команда выполняет запрос и возвращает **XmlReader**, необходимо проанализировать данные и метаданные. Данные и метаданные XML представлены в собственном формате, используемом поставщиком XML для аналитики. Для большинства поставщиков XML для аналитики, собственный формат может **MDDataSet** формат. **MDDataSet** формат обеспечивает данные и метаданные наборов ячеек в хорошо структурированной форме. Дополнительные сведения о **MDDataSet** форматирования см. в разделе спецификации XML для аналитики.  
  
3.  **Закройте средство чтения.**  
  
     Следует всегда вызывать <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> метод завершения с помощью **XmlReader** объекта. Хотя **XmlReader** открыт, **XmlReader** имеет монопольное право на использование <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> объект, который был использован для выполнения команды. Вы не сможете выполнять любые команды, с помощью, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, включая создание другого **XmlReader** или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, пока не закрыт исходный **XmlReader**.  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>Пример получения данных из объекта XmlReader  
 В следующем примере выполняется команда и получает данные в виде **XmlReader**, выводя содержимое файла на консоль.  
  
 [!code-cs[Adomd.NetClient#OutputDataWithXML](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-data-using-th_1_1.cs)]  
  
## <a name="see-also"></a>См. также:  
 [Получение данных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)   
 [Получение данных с помощью набора ячеек](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)   
 [Получение данных с помощью объекта AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)  
  
  
