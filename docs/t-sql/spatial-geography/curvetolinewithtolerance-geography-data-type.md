---
title: CurveToLineWithTolerance (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CurveToLineWithTolerance_TSQL
- CurveToLineWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- CurveToLineWithTolerance method (geography)
ms.assetid: 74369c76-2cf6-42ae-b9cc-e7a051db2767
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6f81b5ba7ba6de057dd82090775013db55e4275b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68066492"
---
# <a name="curvetolinewithtolerance-geography-data-type"></a>CurveToLineWithTolerance (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает приближение из многоугольников для экземпляра **geography**, содержащего сегменты дуги.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.CurveToLineWithTolerance( tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
_tolerance_  
Выражение типа **double**, которое определяет максимальную ошибку между исходным сегментом дуги и его линейной аппроксимацией.  
  
_relative_  
Представляет собой выражение типа **bool**, указывающее, следует ли использовать относительный максимум для отклонения. Если относительный параметр принимает значение false (0), для абсолютного максимума устанавливается значение, равное возможному отклонению линейной аппроксимации. Если относительный параметр принимает значение true, то вычисляется погрешность, равная произведению параметра tolerance на диаметр ограничивающего прямоугольника для пространственного объекта.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
Если установить погрешность <= 0, возникнет исключение **ArgumentOutOfRange**.  
  
## <a name="remarks"></a>Remarks  
Этот метод позволяет указывать допустимое количество ошибок для результирующего объекта **LineString**.  
  
Метод **CurveToLineWithTolerance** вернет экземпляр **LineString** для экземпляра **CircularString** или **CompoundCurve** и экземпляр **Polygon** для экземпляра **CurvePolygon**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Использование различных значений погрешности в экземпляре CircularString  
В следующем примере показано, каким образом задание погрешности влияет на экземпляр `LineString`, возвращаемый из экземпляра `CircularString`:  
  
```
DECLARE @g geography;  
SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();
```  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>Б. Использование метода в экземпляре MultiLineString, содержащем один элемент LineString  
Следующий пример показывает, что возвращается из экземпляра `MultiLineString`, который содержит только один экземпляр `LineString`:  
  
```
DECLARE @g geography;  
SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649))');  
SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
```  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>В. Использование метода в экземпляре MultiLineString, содержащем несколько элементов LineString  
Следующий пример показывает, что возвращается из экземпляра `MultiLineString`, который содержит более одного экземпляра `LineString`:  
  
```
DECLARE @g geography;  
SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649),(-123.358 47.653, -123.348 47.649))');  
SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
```  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>Г. Установка параметра relative в значение true для вызова экземпляра CurvePolygon  
В следующем примере используется экземпляр `CurvePolygon` для вызова `CurveToLineWithTolerance()` с параметром *relative*, имеющим значение true:  
  
```
DECLARE @g geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658), (-122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
```  
  
## <a name="see-also"></a>См. также:  
[Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
