---
description: CurveToLineWithTolerance (тип данных geometry)
title: CurveToLineWithTolerance (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CurveToLineWithTolerance method (geometry)
ms.assetid: 96871075-1998-4cd9-86b1-3fc55577aee4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4a717b5b83be8d381a91ff1ab1055d24ae8c59ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488227"
---
# <a name="curvetolinewithtolerance-geometry-data-type"></a>CurveToLineWithTolerance (тип данных geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Возвращает приближение из многоугольников для экземпляра **geometry**, содержащего сегменты дуги.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.CurveToLineWithTolerance ( tolerance, relative )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *tolerance*  
 Выражение типа **double**, которое определяет максимальную ошибку между исходным сегментом дуги и его линейной аппроксимацией.  
  
 *relative*  
 Представляет собой выражение типа **bool**, указывающее, следует ли использовать относительный максимум для отклонения. Когда для относительного параметра задается значение false (0), для абсолютного максимума устанавливается значение, равное возможному отклонению линейной аппроксимации. Если для относительного параметра задано значение true, то вычисляется погрешность, равная произведению параметра tolerance на диаметр ограничивающего прямоугольника для пространственного объекта.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 При задании tolerance <= 0 возникает исключение `ArgumentOutOfRange`.  
  
## <a name="remarks"></a>Комментарии  
 В этом методе можно указывать допустимое количество ошибок для результирующего объекта **LineString**.  
  
 В следующей таблице показан тип экземпляра, который возвращается методом `CurveToLineWithTolerance()` для различных типов.  
  
|Тип вызывающего экземпляра|Возвращенный пространственный тип|  
|----------------------------|---------------------------|  
|Пустой экземпляр геометрического объекта|Пустой экземпляр **GeometryCollection**|  
|**Point** и **MultiPoint**|Экземпляр **Point**|  
|**MultiPoint**|Экземпляр **Point** или **MultiPoint**|  
|**CircularString**, **CompoundCurve** или **LineString**|Экземпляр **LineString**|  
|**MultiLineString**|Экземпляр **LineString** или **MultiLineString**|  
|**CurvePolygon** и **Polygon**|Экземпляр **Polygon**|  
|**MultiPolygon**|Экземпляр **Polygon** или **MultiPolygon**|  
|**GeometryCollection** с одним экземпляром, который не содержит сегмент дуги|Экземпляр, который находится в коллекции **GeometryCollection**, определяет тип возвращаемого экземпляра.|  
|**GeometryCollection** с одним одномерным экземпляром сегмента дуги (**CircularString**, **CompoundCurve**)|Экземпляр **LineString**|  
|**GeometryCollection** с одним двухмерным экземпляром сегмента дуги (**CurvePolygon**)|Экземпляр **Polygon**|  
|**GeometryCollection** с несколькими одномерными экземплярами|Экземпляр **MultiLineString**|  
|**GeometryCollection** с несколькими двухмерными экземплярами|Экземпляр **MultiPolygon**|  
|**GeometryCollection** с несколькими экземплярами разных размерностей|Экземпляр **GeometryCollection**|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Использование различных значений погрешности в экземпляре CircularString  
 В следующем примере показано, каким образом задание погрешности влияет на экземпляр `LineString`, возвращаемый из экземпляра `CircularString`:  
  
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
 В следующем примере используется экземпляр `CurvePolygon` для вызова `CurveToLineWithTolerance()` с параметром *relative*, имеющим значение true:  
  
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
 [CurveToLineWithTolerance (тип данных geography)](../../t-sql/spatial-geography/curvetolinewithtolerance-geography-data-type.md)   
 [STCurveToLine (тип данных geometry)](../../t-sql/spatial-geometry/stcurvetoline-geometry-data-type.md)  
  
  

