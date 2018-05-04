---
title: Получение данных с помощью XmlReader | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43ce3cda885ec3583fb69d565b5dae875b492db6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-data-using-the-xmlreader"></a>Получение данных с помощью объекта XmlReader
  **XmlReader** класса часть **System.Xml** пространство имен для библиотеки классов Microsoft .NET Framework аналогично <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> класса в том, что **XmlReader**класс также предоставляет быстрый некэшируемый однопроходный доступ к данным. Если нет необходимости для представления в памяти и аналитических данных с помощью <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> объекта, **XmlReader** объекта идеально подходит для получения XML-данных, особенно для больших объемов данных. Поскольку **XmlReader** потоки данных, **XmlReader** не должен получать и кэшировать все данные перед передачей вызывающему объекту, как было бы в том случае, если <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> объекта были использованы для преобразования Ответ XML для аналитики в аналитическое представление модели объектов.  
  
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
  
## <a name="see-also"></a>См. также  
 [Получение данных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)   
 [Получение данных с помощью набора ячеек](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)   
 [Получение данных с помощью объекта AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)  
  
  
