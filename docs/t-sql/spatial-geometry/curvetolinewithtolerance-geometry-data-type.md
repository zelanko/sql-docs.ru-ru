---
title: "CurveToLineWithTolerance (тип данных geometry) | Документы Microsoft"
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
helpviewer_keywords: CurveToLineWithTolerance method (geometry)
ms.assetid: 96871075-1998-4cd9-86b1-3fc55577aee4
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9fd46759735549e06a25544ee04a4db356464916
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="curvetolinewithtolerance-geometry-data-type"></a>CurveToLineWithTolerance (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает приближение из многоугольников **geometry** экземпляра, содержащего сегменты дуги.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.CurveToLineWithTolerance ( tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
 *отказоустойчивость*  
 — **Двойные** выражение, определяющее максимальную ошибку между исходным сегментом дуги и его линейной аппроксимацией.  
  
 *relative*  
 — **Bool** выражение, которое указывает, следует ли использовать относительный максимум для отклонения. Когда для относительного параметра задается значение false (0), для абсолютного максимума устанавливается значение, равное возможному отклонению линейной аппроксимации. Если для относительного параметра задано значение true, то вычисляется погрешность, равная произведению параметра tolerance на диаметр ограничивающего прямоугольника для пространственного объекта.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 При задании tolerance <= 0 возникает исключение `ArgumentOutOfRange`.  
  
## <a name="remarks"></a>Remarks  
 Этот метод можно указать допустимое количество ошибок для результирующего **LineString**.  
  
 В следующей таблице показан тип экземпляра, который возвращается методом `CurveToLineWithTolerance()` для различных типов.  
  
|Тип вызывающего экземпляра|Возвращенный пространственный тип|  
|----------------------------|---------------------------|  
|Пустой экземпляр геометрического объекта|Пустой **GeometryCollection** экземпляра|  
|**Точка** и **MultiPoint**|**Точка** экземпляра|  
|**MultiPoint**|**Точка** или **MultiPoint** экземпляра|  
|**CircularString**, **CompoundCurve**, или **LineString**|**LineString** экземпляра|  
|**MultiLineString**|**LineString** или **MultiLineString** экземпляра|  
|**CurvePolygon** и **многоугольника**|**Многоугольник** экземпляра|  
|**MultiPolygon**|**Многоугольник** или **MultiPolygon** экземпляра|  
|**GeometryCollection** для одного экземпляра, который не содержит сегмент дуги|Экземпляр, который содержится в **GeometryCollection** определяет тип возвращаемого экземпляра.|  
|**GeometryCollection** с одним одномерного сегмента экземпляром дуги (**CircularString**, **CompoundCurve**)|**LineString** экземпляра|  
|**GeometryCollection** с экземпляром сегмента один двухмерный дуги (**CurvePolygon**)|**Многоугольник** экземпляра|  
|**GeometryCollection** с несколькими одномерными экземплярами|**MultiLineString** экземпляра|  
|**GeometryCollection** с несколькими двухмерными экземплярами|**MultiPolygon** экземпляра|  
|**GeometryCollection** с несколькими экземплярами разных размерностей|**GeometryCollection** экземпляра|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Использование различных значений погрешности в экземпляре CircularString  
 В следующем примере показано, каким образом задание погрешности влияет на `LineString`экземпляр, возвращаемый из `CircularString` экземпляр:  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();
 ```  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>Б. Использование метода в экземпляре MultiLineString, содержащем один элемент LineString  
 Следующий пример показывает, что возвращается из экземпляра `MultiLineString`, который содержит только один экземпляр `LineString`:  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('MULTILINESTRING((1 3, 4 8, 6 9))'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>В. Использование метода в экземпляре MultiLineString, содержащем несколько элементов LineString  
 Следующий пример показывает, что возвращается из экземпляра `MultiLineString`, который содержит более одного экземпляра `LineString`:  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('MULTILINESTRING((1 3, 4 8, 6 9),(4 4, 9 18))'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>Г. Установка параметра relative в значение true для вызова экземпляра CurvePolygon  
 В следующем примере используется `CurvePolygon` экземпляра для вызова `CurveToLineWithTolerance()` с *относительный* задано значение true:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
 ```  
  
### <a name="e-using-the-method-on-a-geometrycollection-instance"></a>Д. Использование метода с экземпляром GeometryCollection  
 В следующем примере метод `CurveToLineWithTolerance()` вызывается для коллекции `GeometryCollection`, которая содержит двухмерный экземпляр `CurvePolygon` и одномерный экземпляр `CircularString`. Метод `CurveToLineWithTolerance()` преобразует оба типа сегментов дуги в типы линейных сегментов и возвращает их в виде типа `GeometryCollection`.  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('GEOMETRYCOLLECTION(CURVEPOLYGON( COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))), CIRCULARSTRING(4 4, 8 6, 9 5))'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.1, 0).ToString();
 ```  
  
## <a name="see-also"></a>См. также  
 [CurveToLineWithTolerance &#40; тип данных geography &#41;](../../t-sql/spatial-geography/curvetolinewithtolerance-geography-data-type.md)   
 [STCurveToLine &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stcurvetoline-geometry-data-type.md)  
  
  

