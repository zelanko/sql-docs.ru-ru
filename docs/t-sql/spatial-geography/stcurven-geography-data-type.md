---
title: STCurveN (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveN
- STCurveN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 19aec9ae5a0253e74ff8816fadcfdbb7a2a74001
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68042448"
---
# <a name="stcurven-geography-data-type"></a>STCurveN (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает кривую, указанную в экземпляре **geography** типа **LineString**, **CircularString** или **CompoundCurve**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 Выражение типа **int** со значением в диапазоне от 1 до числа кривых в экземпляре **geography**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Если n < 1, возникает исключение **ArgumentOutOfRangeException**.  
  
## <a name="remarks"></a>Remarks  
 Значение **NULL** возвращается при возникновении указанных ниже условий.  
  
-   Экземпляр **geography** объявлен, но не создан.  
  
-   Экземпляр **geography** пуст.  
  
-   n превышает число кривых в экземпляре **geography** (см. статью [STNumCurves (тип данных geography)](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)  
  
-   Неравенство измерения для экземпляра **geography** (см. статью [STDimension (тип данных geography)](../../t-sql/spatial-geography/stdimension-geography-data-type.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>A. Применение метода STCurveN() к объекту CircularString  
 В приведенном ниже примере возвращается вторая кривая в экземпляре **CircularString**.  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Пример возвращает управление.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>Б. Применение метода STCurveN() к объекту CompoundCurve  
 В приведенном ниже примере возвращается вторая кривая в экземпляре **CompoundCurve**.  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Пример возвращает управление.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>В. Применение метода STCurveN() к объекту CompoundCurve, содержащему три объекта CircularString  
 В приведенном ниже примере используется экземпляр **CompoundCurve**, в котором три отдельных экземпляра **CircularString** объединяются в одной последовательности кривых, как в предыдущем примере.  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Пример возвращает управление.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()` возвращает одинаковые результаты независимо от используемого формата Well-Known Text (WKT).  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>Г. Проверка допустимости перед вызовом метода STCurve()  
 В приведенном ниже примере показано, как проверить допустимость *n* перед вызовом метода STCurveN():  
  
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
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
