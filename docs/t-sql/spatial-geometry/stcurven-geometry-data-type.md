---
title: "STCurveN (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geometry)
ms.assetid: 64adf1a1-3a41-41fb-b7d1-44390c3e4ea9
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd5b459bfa271d98844d30455e4e1a9e03d0e2cd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stcurven-geometry-data-type"></a>STCurveN (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает кривую, указанную в **geometry** экземпляра, то есть **LineString**, **CircularString**, **CompoundCurve**, или  **MultiLineString**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveN ( curve_index )  
```  
  
## <a name="arguments"></a>Аргументы  
 *curve_index*  
 — **Int** выражение от 1 до числа кривых в **geometry** экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 Если *curve_index* < 1 то `ArgumentOutOfRangeException` возникает исключение.  
  
## <a name="remarks"></a>Замечания  
 **Значение NULL** возвращается, если возникает какое-либо из следующих действий:  
  
-   **geometry** экземпляра объявлен, но не создается  
  
-   **geometry** экземпляр пуст  
  
-   *curve_index* превышает число кривых в **geometry** экземпляра  
  
-   **geometry** экземпляр **точки**, **MultiPoint**, **многоугольника**, **CurvePolygon**, или  **MultiPolygon**  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stcurven-on-a-circularstring-instance"></a>A. Применение STCurveN() к экземпляру CircularString  
 Следующий пример возвращает вторую кривую в экземпляре `CircularString`:  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Приведенный ранее в этом разделе пример возвращает:  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve-instance-with-one-circularstring-instance"></a>Б. Применение STCurveN() к экземпляру CompoundCurve с одним экземпляром CircularString  
 Следующий пример возвращает вторую кривую в экземпляре `CompoundCurve`:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Приведенный ранее в этом разделе пример возвращает:  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-instance-with-three-circularstring-instances"></a>В. Применение STCurveN() к экземпляру CompoundCurve с тремя экземплярами CircularString  
 Следующий пример использует экземпляр `CompoundCurve`, который сочетает три отдельных экземпляра `CircularString` в одной последовательности кривых, как в предыдущем примере:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE (CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246), CIRCULARSTRING(3 6.3246, 0 7, -3 6.3246), CIRCULARSTRING(-3 6.3246, -1 2.1082, 0 0))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Приведенный ранее в этом разделе пример возвращает:  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
 Обратите внимание, что результаты во всех трех предыдущих примерах совпадают. Какой бы формат WKT (Well-known Text) ни использовался для ввода одной и той же последовательности кривой, результаты, возвращаемые `STCurveN()` при использовании экземпляра `CompoundCurve`, будут совпадать.  
  
### <a name="d-validating-the-parameter-before-calling-stcurven"></a>Г. Проверка параметра перед вызовом STCurveN()  
 В следующем примере показано, как убедитесь, что `@n` является допустимым, перед вызовом метода `STCurveN()`метод:  
  
```
 DECLARE @g geometry;  
 DECLARE @n int;  
 SET @n = 3;  
 SET @g = geometry::Parse('CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
 ```  
  
## <a name="see-also"></a>См. также:  
 [STNumCurves &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)   
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


