---
title: "STCurveToLine (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: STCurveToLine method (geometry)
ms.assetid: abc80b32-4152-4e10-b816-798b901e0ac5
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5950ba5609fdd34008c051166f089cf3433890d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stcurvetoline-geometry-data-type"></a>STCurveToLine (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает приближение из многоугольников **geometry** экземпляра, содержащего сегменты дуги.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveToLine ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Возвращает пустую коллекцию **GeometryCollection**экземпляра для пустых **geometry** экземпляра переменных и возвращает **NULL** для неинициализированных **geometry** переменных.  
  
 Приближение из многоугольников, метод возвращает зависит от **geometry** экземпляра, используемого для вызова метода:  
  
-   Возвращает **LineString** экземпляра для **CircularString** или **CompoundCurve** экземпляра.  
  
-   Возвращает **многоугольника** экземпляра для **CurvePolygon** экземпляра.  
  
-   Возвращает копию **geometry** экземпляра, если этот экземпляр не является **CircularString**, **CompoundCurve**, или **CurvePolygon** экземпляра . Например `STCurveToLine` возвращает **точки** экземпляра для **geometry** экземпляра, то есть **точки** экземпляра.  
  
 В отличие от спецификации SQL/MM `STCurveToLine` метод не использует значения по оси z для расчета аппроксимации. Этот метод игнорирует любые значения по оси z, имеющиеся в вызывающем **geometry** экземпляра.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-an-uninitialized-geometry-variable-and-empty-instance"></a>A. Использование неинициализированной переменной геометрии и пустого экземпляра  
 В следующем примере первый **ВЫБЕРИТЕ** инструкция использует неинициализированный **geometry** экземпляра для вызова `STCurveToLine` метода, а вторая **ВЫБЕРИТЕ** Инструкция использует пустой **geometry** экземпляра. Таким образом, метод возвращает **NULL** в первой инструкции и **GeometryCollection** сбора для второй инструкции.  
  
```
 DECLARE @g geometry; 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType(); 
 SET @g = geometry::Parse('LINESTRING EMPTY'); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="b-using-a-linestring-instance"></a>Б. Использование экземпляра объекта LineString  
 **ВЫБЕРИТЕ** инструкции в следующем примере используется **LineString** экземпляра для вызова метода STCurveToLine. Таким образом, метод возвращает **LineString** экземпляра.  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('LINESTRING(1 3, 5 5, 4 3, 1 3)'); 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="c-using-a-circularstring-instance"></a>В. Использование экземпляра объекта CircularString  
 Первый **ВЫБЕРИТЕ** инструкции в следующем примере используется **CircularString** экземпляра для вызова метода STCurveToLine. Таким образом, метод возвращает **LineString** экземпляра. Это **ВЫБЕРИТЕ** инструкции также сравнивает длину двух экземпляров, которые являются приблизительно.  Наконец, вторая **ВЫБЕРИТЕ** инструкция возвращает число точек для каждого экземпляра.  Он возвращает только 5 точек для **CircularString** экземпляр, но 65 точек для **LineString**экземпляра.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type], @g1.STLength() AS [G1 Perimeter], @g2.STLength() AS [G2 Perimeter], @g2.ToString() AS [G2 Def]; 
 SELECT @g1.STNumPoints(), @g2.STNumPoints();
 ```  
  
### <a name="d-using-a-curvepolygon-instance"></a>Г. Использование экземпляра объекта CurvePolygon  
 **ВЫБЕРИТЕ** инструкции в следующем примере используется **CurvePolygon** экземпляра для вызова метода STCurveToLine. Таким образом, метод возвращает **многоугольника** экземпляра.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type];
 ```  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [STLength (тип данных geometry)](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STNumPoints (тип данных geometry)](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STGeometryType (тип данных geometry)](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
  

