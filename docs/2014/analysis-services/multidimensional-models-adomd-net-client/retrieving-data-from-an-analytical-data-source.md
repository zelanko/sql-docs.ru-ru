---
title: Получение данных из источника аналитических данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cfc0c783e8c61689d8f5b0ca3bab6ded39a57a4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212384"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Получение данных из источника аналитических данных
  Установив соединение и создав запрос, можно начать извлечение данных. В ADOMD.NET извлекать данные можно при помощи трех разных объектов (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> и <xref:System.Xml.XmlReader>) путем вызова одного из методов `Execute` объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
 Каждый из этих трех объектов позволяет достичь определенного равновесия между интерактивностью и издержками.  
  
-   *Интерактивные возможности* простоты использования и объем сведений, доступных через объектную модель.  
  
-   *Издержки* ссылается на объем трафика, который создает модель объектов через сетевое подключение к серверу, объем памяти, необходимой для объектной модели, а также скорость, с которой модель объектов извлекает данные.  
  
 В приведенной ниже таблице показаны различия между интерактивностью и издержками для каждого объекта, что позволяет проще выбрать объект для извлечения данных, в наибольшей степени соответствующий потребностям приложения.  
  
|Объект|Интерактивность|Издержки|Сохраняет размерность|Данные об использовании|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Наивысшая|Умеренно высокие, результатом чего является самая низкая скорость извлечения данных|Да|[Получение данных с помощью объекта CellSet](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Средняя|Средняя|Нет|[Заполнение набора данных из объекта DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Средняя|Средняя|Нет|[Получение данных с помощью объекта AdomdDataReader](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Минимальная|Наименьшие, результатом чего является самая высокая скорость извлечения данных|Да|[Получение данных с помощью объекта XmlReader](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>См. также  
 [Программирование клиента ADOMD.NET](adomd-net-client-programming.md)  
  
  
