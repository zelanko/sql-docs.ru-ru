---
title: "BufferWithTolerance (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feaa401cfd6e2077035d164412941392412011ae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает геометрический объект, представляющий объединение всех точек, расстояние которых от **geography** экземпляр меньше или равно указанному значению с указанной погрешностью.  
  
 Это geography, тип данных поддерживает метод **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
 *расстояние*  
 — **Float** выражение, задающее расстояние от **geography** , вокруг которого вычисляется буфер.  
  
 Максимальное расстояние буфера не может превышать 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* 1/2 окружности Земли) или полного земного шара.  
  
 *отказоустойчивость*  
 — **Float** выражение, задающее погрешность расстояния буфера.  
  
 *Отклонения* значение относится к максимальному отклонению в идеальном буферном расстоянии для возвращенной линейной аппроксимации.  
  
 Например, идеальной границей буфера для точки является окружность, однако ее необходимо приблизительно изобразить многоугольником. Чем меньше заданная погрешность, тем из большего числа точек должен состоять многоугольник. Это увеличивает сложность результата, но уменьшает его погрешность.  
  
 Минимальный предел составляет 0,1% от расстояния, и любая меньшая погрешность будет округлена до этого значения.  
  
 *относительный*  
 — **Бит** указание ли *отклонения* значение — относительный или абсолютный. Если 'TRUE' "или" 1 ", относительное и рассчитывается как произведение *отклонения* и углового экстента \* экваториальный радиус эллипсоида. Если значение «FALSE», или 0, погрешность является абсолютной и *отклонения* значение — задает максимальное абсолютное отклонение в идеальном буферном расстоянии для возвращенной линейной аппроксимации.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Этот метод вызывает исключение **ArgumentException** Если *расстояние* не является числом (NAN), или если *расстояние* является положительной или отрицательной бесконечности.  Этот метод также вызывает **ArgumentException** Если *отклонения* является ноль (0), не является числом (NaN), отрицательное, или положительная или отрицательная бесконечность.  
  
 `STBuffer()`Возвращает **FullGlobe** экземпляра в определенных случаях; например, `STBuffer()` возвращает **FullGlobe** экземпляра на двух полюсах, когда буферное расстояние больше, чем расстояние от экватора к полюса.  
  
 Этот метод вызывает исключение **ArgumentException** в **FullGlobe** экземпляров, где расстояние буфера превышает следующее ограничение:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* 1/2 окружности Земли)  
  
 Ошибкой между теоретическим и рассчитанным буфером является max (погрешность, экстентов \* 1.E-7) где значение допуска *отклонения* параметра. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point`, и метод `BufferWithTolerance()` производит получение приблизительного буфера вокруг этого экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STBuffer &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

