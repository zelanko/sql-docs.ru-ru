---
title: STCurveN (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geometry)
ms.assetid: 64adf1a1-3a41-41fb-b7d1-44390c3e4ea9
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f3ed32f720bc565fd50e230b9e209006ccc449ee
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041804"
---
# <a name="stcurven-geometry-data-type"></a>STCurveN (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает кривую, указанную в экземпляре **geometry** типа **LineString**, **CircularString**, **CompoundCurve** или **MultiLineString**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveN ( curve_index )  
```  
  
## <a name="arguments"></a>Аргументы  
 *curve_index*  
 Выражение типа **int** от 1 до количества кривых в экземпляре **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 Если *curve_index* < 1, вызывается исключение `ArgumentOutOfRangeException`.  
  
## <a name="remarks"></a>Remarks  
 Значение **NULL** возвращается при выполнении любого из указанных ниже условий.  
  
-   Экземпляр **geometry** объявлен, но не создан.  
  
-   Экземпляр **geometry** является пустым.  
  
-   *curve_index* превышает число кривых в экземпляре **geometry**.  
  
-   Экземпляр **geometry** относится к типу **Point**, **MultiPoint**, **Polygon**, **CurvePolygon** или **MultiPolygon**.  
  
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
 В приведенном ниже примере показано, как проверить допустимость `@n` перед вызовом метода `STCurveN()`.  
  
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
 [STNumCurves (тип данных geometry)](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

