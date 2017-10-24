---
title: "STCurveN (тип данных geography) | Документы Microsoft"
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
- STCurveN
- STCurveN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d33b8e6752ac8aca3bc6846a4558af4830373081
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stcurven-geography-data-type"></a>STCurveN (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает кривую, указанную в **geography** экземпляра, то есть **LineString**, **CircularString**, или **CompoundCurve**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 — **Int** выражение от 1 до числа кривых в **geography** экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Если n < 1 то **ArgumentOutOfRangeException** возникает исключение.  
  
## <a name="remarks"></a>Замечания  
 **Значение NULL** возвращается при возникновении следующих условий.  
  
-   **Geography** экземпляр объявлен, но не создан  
  
-   **Geography** экземпляр пуст  
  
-   n превышает число кривых в **geography** экземпляра (в разделе [STNumCurves &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)  
  
-   Измерение для **geography** экземпляр не равен (см. [STDimension &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stdimension-geography-data-type.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>A. Применение метода STCurveN() к объекту CircularString  
 Следующий пример возвращает вторую кривую в **CircularString** экземпляр:  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Пример возвращает управление.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>Б. Применение метода STCurveN() к объекту CompoundCurve  
 Следующий пример возвращает вторую кривую в **CompoundCurve** экземпляр:  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Пример возвращает управление.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>В. Применение метода STCurveN() к объекту CompoundCurve, содержащему три объекта CircularString  
 В следующем примере используется **CompoundCurve** экземпляр, который сочетает три отдельных **CircularString** экземпляров в один последовательности кривых, как в предыдущем примере:  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Пример возвращает управление.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()` возвращает одинаковые результаты независимо от используемого формата Well-Known Text (WKT).  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>Г. Проверка допустимости перед вызовом метода STCurve()  
 В следующем примере показано, как убедиться, что  *n*  является допустимым, перед вызовом метода STCurveN():  
  
```
 DECLARE @g geography;  
 DECLARE @n int;  
 SET @n = 2;  
 SET @g = geography::Parse('LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
  ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

