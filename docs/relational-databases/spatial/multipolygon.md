---
title: MultiPolygon | Microsoft Docs
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8522e65762e8c27ec65fb5fc4a56db0653b5f5c9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72907009"
---
# <a name="multipolygon"></a>MultiPolygon
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Экземпляр **MultiPolygon** представляет собой коллекцию экземпляров **Polygon** .  
  
## <a name="polygon-instances"></a>Экземпляры многоугольников  
 На рисунке ниже приведены примеры экземпляров **MultiPolygon** .  
  
 ![Примеры экземпляров MultiPolygon типа geometry](../../relational-databases/spatial/media/multipolygon.gif "Примеры экземпляров MultiPolygon типа geometry")  
  
 На рисунке представлены:  
  
-   1 — экземпляр типа **MultiPolygon** с двумя элементами **Polygon** . Граница определяется двумя внешними кольцами и тремя внутренними кольцами.  
  
-   2 — экземпляр типа **MultiPolygon** с двумя элементами **Polygon** . Граница определяется двумя внешними кольцами и тремя внутренними кольцами. Два элемента **Polygon** пересекаются в точке касания.  
  
### <a name="accepted-instances"></a>Принимаемые экземпляры  
 Экземпляр **MultiPolygon** является принимаемым, если истинно одно из следующих условий.  
  
-   Это пустой экземпляр **MultiPolygon** .  
  
-   Все экземпляры, составляющие экземпляр **MultiPolygon** , являются принимаемыми экземплярами **Polygon** . Дополнительные сведения о принимаемых экземплярах **Polygon** см. в разделе [Polygon](../../relational-databases/spatial/polygon.md).  
  
В следующих примерах показаны принимаемые экземпляры **MultiPolygon** .  
  
```sql  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
В следующем примере показан экземпляр MultiPolygon, который вызывает исключение `System.FormatException`.  
  
```sql  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
Второй экземпляр в MultiPolygon — это экземпляр LineString, не является принимаемым экземпляром Polygon.  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Экземпляр **MultiPolygon** является допустимым, если это пустой экземпляр **MultiPolygon** или удовлетворяет следующим требованиям.  
  
1.  Все экземпляры, составляющие экземпляр **MultiPolygon** , являются допустимыми экземплярами **Polygon** . Сведения о допустимых экземплярах **Polygon** см. в разделе [Polygon](../../relational-databases/spatial/polygon.md).  
  
2.  Никакие экземпляры **Polygon** , составляющие экземпляр **MultiPolygon** , не перекрываются.  

В следующем примере показаны два допустимых экземпляра **MultiPolygon** и один недопустимый экземпляр **MultiPolygon** .  
  
```sql  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
`@g2` допустим, поскольку два экземпляра **Polygon** имеют только общую точку касания. `@g3` недопустим, поскольку внутренние области экземпляров **Polygon** перекрываются.  
  
## <a name="examples"></a>Примеры  
### <a name="example-a"></a>Пример А.
Следующий пример демонстрирует создание экземпляра `geometry``MultiPolygon` и возвращает второй компонент в формате Well-Known Text (WKT).  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
## <a name="example-b"></a>Пример Б.
В данном примере создается пустой экземпляр `MultiPolygon` .  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## <a name="see-also"></a>См. также:  
 [Polygon](../../relational-databases/spatial/polygon.md)   
 [STArea (тип данных geometry)](../../t-sql/spatial-geometry/starea-geometry-data-type.md)   
 [STCentroid (тип данных geometry)](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)   
 [STPointOnSurface (тип данных geometry)](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
