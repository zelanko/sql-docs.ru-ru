---
title: Получение данных из источника аналитических данных | Документы Microsoft
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
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6e6243a815b399c91a2cd7aaa9eca712c6c569bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086767"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Получение данных из источника аналитических данных
  Установив соединение и создав запрос, можно начать извлечение данных. В ADOMD.NET извлекать данные можно при помощи трех разных объектов (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> и <xref:System.Xml.XmlReader>) путем вызова одного из методов `Execute` объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
 Каждый из этих трех объектов позволяет достичь определенного равновесия между интерактивностью и издержками.  
  
-   *Интерактивные возможности* относится к простота использования и объем данных, доступных через объектную модель.  
  
-   *Издержки* означает объем трафика, который создает модель объектов по сетевому подключению к серверу, объем памяти, необходимый для объектной модели, а также скорости, с которой модель объектов извлекает данные.  
  
 В приведенной ниже таблице показаны различия между интерактивностью и издержками для каждого объекта, что позволяет проще выбрать объект для извлечения данных, в наибольшей степени соответствующий потребностям приложения.  
  
|Объект|Интерактивность|Издержки|Сохраняет размерность|Данные об использовании|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Наивысшая|Умеренно высокие, результатом чего является самая низкая скорость извлечения данных|Да|[Получение данных с помощью объекта CellSet](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Средняя|Средняя|Нет|[Заполнение набора данных с помощью DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Средняя|Средняя|Нет|[Получение данных с помощью объекта AdomdDataReader](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Минимальная|Наименьшие, результатом чего является самая высокая скорость извлечения данных|Да|[Получение данных с помощью объекта XmlReader](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>См. также  
 [Программирование клиента ADOMD.NET](adomd-net-client-programming.md)  
  
  