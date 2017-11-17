---
title: "BufferWithTolerance (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- BufferWithTolerance (geometry Data Type)
ms.assetid: 7049d37a-3e72-4e93-87a1-c96a6f0e2b99
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ffa8a350cb4531f9d4a6d1439a4dad0682189266
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geometry-data-type"></a>BufferWithTolerance (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает геометрический объект, представляющий объединение всех точек, расстояние которых от **geometry** экземпляр меньше или равно указанному значению с указанной погрешностью.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
 *расстояние*  
 — **Float** выражение, задающее расстояние от **geometry** , вокруг которого вычисляется буфер.  
  
 *отказоустойчивость*  
 — **Float** выражение, задающее погрешность расстояния буфера.  
  
 *Отклонение* относится к максимальному отклонению в идеальном буферном расстоянии для возвращенной линейной аппроксимации.  
  
 Например, идеальной границей буфера для точки является окружность, однако ее необходимо приблизительно изобразить многоугольником. Чем меньше заданная погрешность, тем из большего числа точек должен состоять многоугольник. Это увеличивает сложность результата, но уменьшает его погрешность.  
  
 *относительный*  
 — **Бит** указание ли *отклонения* значение — относительный или абсолютный. Если «TRUE» или 1, затем отклонения относительное и рассчитывается как произведение *отклонения* и диаметра ограничивающего прямоугольника экземпляра. Если значение «FALSE», или 0, погрешность является абсолютной и *отклонения* значение — задает максимальное абсолютное отклонение в идеальном буферном расстоянии для возвращенной линейной аппроксимации.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 *Отклонения* параметр должен быть больше нуля. Если *отклонения* < = 0 то `System.ArgumentOutOfRangeException` возникает исключение.  
  
> [!NOTE]  
>  Поскольку *отклонения* — **float** типа, `System.Runtime.InteropServices.COMException` выводится, если значение, заданное в качестве допуска очень мал из-за особенностей округления типов с плавающей запятой.  
  
## <a name="remarks"></a>Замечания  
 Когда *расстояние* > 0, то **многоугольника** или **MultiPolygon** возвращается экземпляр.  
  
> [!NOTE]  
>  Поскольку аргумент distance относится **float**, очень маленькое значение может быть приравнено к нулю в вычислениях. Когда это происходит, копия вызывающего **geometry** возвращается экземпляр. В разделе [float и real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Когда *расстояние* = 0, то копия вызывающего **geometry** возвращается экземпляр.  
  
 Когда *расстояние* < 0, то  
  
-   Пустой **GeometryCollection** экземпляр возвращается в том случае, если измерений экземпляра 0 или 1.  
  
-   Возвращается отрицательный буфер, если измерений экземпляра 2 или более.  
  
    > [!NOTE]  
    >  Отрицательный буфер может также создать пустой **GeometryCollection** экземпляра.  
  
 Отрицательный буфер удаляет все точки в пределах заданного расстояния от границы **geometry** экземпляра.  
  
 Ошибкой между теоретическим и рассчитанным буфером является max (погрешность, экстентов \* 1.E-7) где значение допуска *отклонения* параметра. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geometry](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point`, и метод `BufferWithTolerance()` производит получение приблизительного буфера вокруг этого экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 3)', 0);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STBuffer &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


