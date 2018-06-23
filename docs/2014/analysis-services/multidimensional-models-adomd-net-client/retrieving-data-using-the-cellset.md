---
title: Получение данных с помощью набора ячеек | Документы Microsoft
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
- CellSet object
- retrieving data
- data retrieval [ADOMD.NET], CellSet object
ms.assetid: 77e4ee58-882d-4012-91a3-0565f18a4882
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cda35dc6151d17e1dad2d341337d67ef39d9f839
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100735"
---
# <a name="retrieving-data-using-the-cellset"></a>Получение данных с помощью объекта CellSet
  Объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> является наиболее интерактивным и гибким, если требуется извлечение аналитических данных. Объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> является расположенным в памяти кэшем иерархических данных и метаданных, сохраняющим исходную размерность данных. Объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> можно также просматривать в состоянии с установленным или отключенным соединением. Благодаря возможности работать в состоянии с отключенным соединением, объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> можно использовать для просмотра данных и метаданных в любом порядке, кроме того, он предоставляет наиболее полную модель объектов для получения данных. Из-за возможности работать в состоянии с отключенным соединением использование объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> ведет к наибольшим издержкам, поэтому он является наиболее медленной моделью объектов для получения данных в ADOMD.NET.  
  
## <a name="retrieving-data-in-a-connected-state"></a>Извлечение данных в состоянии с установленным соединением  
 Чтобы получить данные с помощью объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, выполните следующие действия.  
  
1.  **Создайте новый экземпляр объекта.**  
  
     Чтобы вызвать новый экземпляр объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, необходимо вызвать метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Идентифицируйте метаданные.**  
  
     Помимо извлечения данных, компонент ADOMD.NET извлекает также метаданные для набора ячеек. После выполнения командой запроса и возвращения объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> метаданные можно извлечь при помощи различных объектов. Клиентскому приложению эти метаданные необходимы для отображения и взаимодействия с данными набора ячеек. Например, многие клиентские приложения имеют функции для детализации или иерархического отображения дочерних позиций указанной позиции в наборе ячеек.  
  
     В компоненте ADOMD.NET свойства <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Axes%2A> и <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.FilterAxis%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> в возвращенном наборе ячеек представляют метаданные осей запроса и среза соответственно. Оба свойства возвращают ссылки на объекты <xref:Microsoft.AnalysisServices.AdomdClient.Axis>, которые, в свою очередь, содержат позиции, представленные на каждой оси.  
  
     Каждый объект <xref:Microsoft.AnalysisServices.AdomdClient.Axis> содержит коллекцию объектов <xref:Microsoft.AnalysisServices.AdomdClient.Position>, представляющую набор кортежей, доступных для этой оси. Каждый объект <xref:Microsoft.AnalysisServices.AdomdClient.Position> представляет один кортеж, который содержит один или несколько элементов, представленных коллекцией объектов <xref:Microsoft.AnalysisServices.AdomdClient.Member>.  
  
3.  **Получение данных из коллекции наборов строк.**  
  
     Помимо извлечения метаданных, компонент ADOMD.NET извлекает также данные для набора ячеек. После выполнения командой запроса и возвращения объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> данные можно извлечь при помощи коллекции <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>. Эта коллекция содержит значения, которые вычисляются для пересечения всех осей в запросе. Поэтому существует несколько индексаторов для доступа к каждому пересечению, или ячейке. Список индексаторов см. в разделе <xref:Microsoft.AnalysisServices.AdomdClient.CellCollection.Item%2A>.  
  
### <a name="example-of-retrieving-data-in-a-connected-state"></a>Пример извлечения данных в состоянии с установленным соединением  
 В следующем примере устанавливается соединение с локальными сервером, а затем выполняется команда для коллекции. Синтаксический анализ результатов в примере выполняется с помощью объектной модели `CellSet`: заголовки (метаданные) для столбцов извлекаются из первой оси, заголовки (метаданные) для каждой строки — из второй оси, а пересекающиеся данные — с помощью коллекции <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A>.  
  
 [!code-csharp[Adomd.NetClient#ReturnCommandUsingCellSet](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#returncommandusingcellset)]  
  
## <a name="retrieving-data-in-a-disconnected-state"></a>Извлечение данных в состоянии с отключенным соединением  
 Объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> можно использовать для предоставления полного метода обзора аналитических данных, не требующего наличия активного соединения, путем загрузки кода XML, возвращенного из предыдущего запроса.  
  
> [!NOTE]  
>  При отключенном состоянии можно использовать не все свойства объектов, доступных из объекта <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>. Дополнительные сведения см. в разделе <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>.  
  
### <a name="example-of-retrieving-data-in-a-disconnected-state"></a>Пример извлечения данных в состоянии с отключенным соединением  
 Следующий пример похож на примеры с метаданными и данными, приведенные ранее в этом разделе. Однако в следующем примере команда выполняется с вызовом метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>, а результат возвращается в виде `System.Xml.XmlReader`. Затем в примере объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> заполняется при помощи этого `System.Xml.XmlReader` с использованием метода <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>. Несмотря на то, что в этом примере `System.Xml.XmlReader` загружается немедленно, код XML, содержащийся в модуле чтения, можно кэшировать на жестком диске или переместить эти данные в другое приложение с использованием любых средств перед загрузкой данных в набор строк.  
  
 [!code-csharp[Adomd.NetClient#DemonstrateDisconnectedCellset](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#demonstratedisconnectedcellset)]  
  
## <a name="see-also"></a>См. также  
 [Получение данных из источника аналитических данных](retrieving-data-from-an-analytical-data-source.md)   
 [Получение данных с помощью объекта AdomdDataReader](retrieving-data-using-the-adomddatareader.md)   
 [Получение данных с помощью объекта XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  