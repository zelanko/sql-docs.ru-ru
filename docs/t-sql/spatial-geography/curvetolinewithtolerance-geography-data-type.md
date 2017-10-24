---
title: "CurveToLineWithTolerance (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CurveToLineWithTolerance_TSQL
- CurveToLineWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- CurveToLineWithTolerance method (geography)
ms.assetid: 74369c76-2cf6-42ae-b9cc-e7a051db2767
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 712ba7cb9705769ae805503a47880d5f349351d1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="curvetolinewithtolerance-geography-data-type"></a>CurveToLineWithTolerance (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает приближение из многоугольников **geography** экземпляра, содержащего сегменты дуги.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.CurveToLineWithTolerance( tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
 *отказоустойчивость*  
 — **Двойные** выражение, определяющее максимальную ошибку между исходным сегментом дуги и его линейной аппроксимацией.  
  
 *относительный*  
 — **Bool** выражение, указывающее, следует ли использовать относительный максимум для отклонения. Когда для относительного параметра задается значение false (0), для абсолютного максимума устанавливается значение, равное возможному отклонению линейной аппроксимации.  Если для относительного параметра задано значение true, то вычисляется погрешность, равная произведению параметра tolerance на диаметр ограничивающего прямоугольника для пространственного объекта.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Задании tolerance < = 0 возникает исключение **ArgumentOutOfRange** исключение.  
  
## <a name="remarks"></a>Замечания  
 Этот метод позволяет указывать для результирующего допустимое количество ошибок **LineString**.  
  
 **CurveToLineWithTolerance** метод будет возвращать **LineString** экземпляра для **CircularString** или **CompoundCurve** экземпляра и **Многоугольника** экземпляра для **CurvePolygon** экземпляра.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Использование различных значений погрешности в экземпляре CircularString  
 В следующем примере показано, каким образом задание погрешности влияет на `LineString`экземпляр, возвращаемый из `CircularString` экземпляр:  
  
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
 В следующем примере используется `CurvePolygon` экземпляра для вызова `CurveToLineWithTolerance()` с *относительный* задано значение true:  
  
 ```
 DECLARE @g geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658), (-122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
 SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

