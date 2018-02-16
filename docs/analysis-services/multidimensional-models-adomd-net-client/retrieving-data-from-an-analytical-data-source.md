---
title: "Получение данных из источника аналитических данных | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 215310100f5151b20e8d813e49c54c056a9e760d
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Получение данных из источника аналитических данных
  Установив соединение и создав запрос, можно начать извлечение данных. В ADOMD.NET можно получить с помощью трех разных объектов данных (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, и <xref:System.Xml.XmlReader>) путем вызова одного из **Execute** методы <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> объекта.  
  
 Каждый из этих трех объектов позволяет достичь определенного равновесия между интерактивностью и издержками.  
  
-   *Интерактивные возможности* относится к простота использования и объем данных, доступных через объектную модель.  
  
-   *Издержки* означает объем трафика, который создает модель объектов по сетевому подключению к серверу, объем памяти, необходимый для объектной модели, а также скорости, с которой модель объектов извлекает данные.  
  
 В приведенной ниже таблице показаны различия между интерактивностью и издержками для каждого объекта, что позволяет проще выбрать объект для извлечения данных, в наибольшей степени соответствующий потребностям приложения.  
  
|Объект|Интерактивность|Издержки|Сохраняет размерность|Данные об использовании|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Наивысшая|Умеренно высокие, результатом чего является самая низкая скорость извлечения данных|Да|[Получение данных с помощью объекта CellSet](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Средняя|Средняя|нет|[Заполнение набора данных с помощью DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Средняя|Средняя|нет|[Получение данных с помощью объекта AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Минимальная|Наименьшие, результатом чего является самая высокая скорость извлечения данных|Да|[Получение данных с помощью объекта XmlReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>См. также  
 [Программирование клиента ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
