---
title: MultiLineString | Документация Майкрософт
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c755752aaa2e4cac795b277c0cdba070d7b2f6d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524189"
---
# <a name="multilinestring"></a>MultiLineString
  Объект `MultiLineString` является коллекцией из нуля или более `geometry` или **geographyLineString** экземпляров.  
  
## <a name="multilinestring-instances"></a>Экземпляры MultiLineString  
 На рисунке ниже приведены примеры экземпляров `MultiLineString`.  
  
 ![Примеры геометрических экземпляров MultiLineString](../../database-engine/media/multilinestring.gif "Примеры геометрических экземпляров MultiLineString")  
  
 На рисунке представлены:  
  
-   Рис. 1 — это простой `MultiLineString` экземпляра, граница которого определяется четырьмя конечными точками двух его `LineString` элементов.  
  
-   Изображение 2 представляет простой экземпляр `MultiLineString`, поскольку пересекаются только конечные точки элементов `LineString`. Граница образована двумя неперекрывающимися конечными точками.  
  
-   Изображение 3 представляет непростой экземпляр `MultiLineString`, поскольку имеется пересечение внутренней части одного из элементов `LineString` этого экземпляра. Границей данного экземпляра `MultiLineString` являются четыре конечные точки.  
  
-   На рисунке 4 представлен отличный от простого незамкнутый экземпляр объекта `MultiLineString`.  
  
-   Изображение 5 представляет простой, незамкнутый экземпляр `MultiLineString`. Не закрыта, поскольку его `LineStrings` элементы не закрыты. Экземпляр является простым, поскольку внутренние стороны экземпляров `LineStrings` не пересекаются.  
  
-   Изображение 6 представляет простой, замкнутый экземпляр `MultiLineString`. Экземпляр является замкнутым, поскольку все его элементы замкнуты. Экземпляр является простым, поскольку внутренние области его элементов не пересекаются.  
  
### <a name="accepted-instances"></a>Правильные экземпляры  
 Чтобы экземпляр `MultiLineString` был принят, он должен либо быть пустым, либо содержать только принимаемые экземпляры `LineString`. Дополнительные сведения о принимаемых `LineString` экземпляров, см. в разделе [LineString](../spatial/linestring.md). В следующих примерах показаны принятые экземпляры `MultiLineString`.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 Следующий пример формирует исключение `System.FormatException`, так как второй экземпляр `LineString` недействителен.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Чтобы экземпляр `MultiLineString` был действителен, он должен соответствовать следующим критериям.  
  
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
  
 Значение `@g4` является недействительным, так как второй экземпляр `LineString` пересекается с первым экземпляром `LineString` на интервале. Они соприкасаются в бесконечном количестве точек.  
  
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
  
  
