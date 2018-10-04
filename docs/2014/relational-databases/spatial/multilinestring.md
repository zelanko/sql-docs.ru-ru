---
title: MultiLineString | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 053af2980857e1bde0ea4b3812b64a276ee9e171
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157264"
---
# <a name="multilinestring"></a>MultiLineString
  Объект `MultiLineString` является коллекцией из нуля или более `geometry` или **geographyLineString** экземпляров.  
  
## <a name="multilinestring-instances"></a>Экземпляры MultiLineString  
 На рисунке ниже показаны примеры `MultiLineString` экземпляров.  
  
 ![Примеры геометрических экземпляров MultiLineString](../../database-engine/media/multilinestring.gif "Примеры геометрических экземпляров MultiLineString")  
  
 На рисунке представлены:  
  
-   Рис. 1 — это простой `MultiLineString` экземпляра, граница которого определяется четырьмя конечными точками двух его `LineString` элементов.  
  
-   Изображение 2 представляет простой экземпляр `MultiLineString`, поскольку пересекаются только конечные точки элементов `LineString`. Граница образована двумя неперекрывающимися конечными точками.  
  
-   Изображение 3 представляет непростой экземпляр `MultiLineString`, поскольку имеется пересечение внутренней части одного из элементов `LineString` этого экземпляра. Границей данного `MultiLineString` экземпляра являются четыре конечные точки.  
  
-   На рисунке 4 представлен отличный от простого незамкнутый `MultiLineString` экземпляра.  
  
-   Изображение 5 представляет простой, незамкнутый экземпляр `MultiLineString`. Не закрыта, поскольку его `LineStrings` элементы не закрыты. Это просто, поскольку внутренние стороны любого из `LineStrings` пересекаются.  
  
-   Рис. 6 представляет простой, закрыто `MultiLineString` экземпляра. Экземпляр является замкнутым, поскольку все его элементы замкнуты. Экземпляр является простым, поскольку внутренние области его элементов не пересекаются.  
  
### <a name="accepted-instances"></a>Правильные экземпляры  
 Для `MultiLineString` экземпляр был принят, он должен либо быть пустым, либо содержать только `LineString` принимаемые экземпляры приняты. Дополнительные сведения о принимаемых `LineString` экземпляров, см. в разделе [LineString](../spatial/linestring.md). В следующих примерах показаны принятые экземпляры `MultiLineString`.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 В следующем примере возникает исключение `System.FormatException` так как второй `LineString` экземпляр является недопустимым.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Для `MultiLineString` экземпляр был допустимым, он должен удовлетворять следующим условиям:  
  
1.  Все экземпляры, составляющие экземпляр `MultiLineString`, должны быть действительными экземплярами `LineString`.  
  
2.  Никакие два экземпляра `LineString`, составляющие экземпляр `MultiLineString`, не могут перекрывать сами себя на интервале. Экземпляры `LineString` могут взаимодействовать или соприкасаться только с собой или с другими экземплярами `LineString` в конечном числе точек.  
  
 В следующем примере показаны три действительных экземпляра `MultiLineString` и один экземпляр `MultiLineString`, который недействителен.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` не допускается из-за второй `LineString` экземпляр пересекается с первым `LineString` экземпляра с интервалом. Они соприкасаются в бесконечном количестве точек.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается простой экземпляр `geometry``MultiLineString` , содержащий два элемента `LineString` со значением SRID 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Чтобы создать экземпляр с другим значением SRID, используйте функции `STGeomFromText()` или `STMLineStringFromText()`. Можно также использовать функцию `Parse()` , а затем изменить SRID, как показано в следующем примере.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>См. также  
 [STLength (тип данных geometry)](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STIsClosed (тип данных geometry)](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [LineString](../spatial/linestring.md)   
 [Пространственные данные (SQL Server)](../spatial/spatial-data-sql-server.md)  
  
  
