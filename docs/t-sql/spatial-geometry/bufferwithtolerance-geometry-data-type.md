---
title: BufferWithTolerance (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 132843721491423d20860ec16e7a8541c7db5668
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33065221"
---
# <a name="bufferwithtolerance-geometry-data-type"></a>BufferWithTolerance (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает геометрический объект, представляющий объединение всех точек, расстояние от которых до указанного экземпляра **geometry** не превышает заданного значения с определенной погрешностью.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
 *distance*  
 Это выражение типа **float** задает расстояние от экземпляра **geometry**, для которого вычисляется буфер.  
  
 *tolerance*  
 Выражение типа **float**, задающее погрешность буферного расстояния.  
  
 Под *погрешностью* понимается максимальное отклонение от идеальной буферной дистанции для возвращаемого линейного приближения.  
  
 Например, идеальной границей буфера для точки является окружность, однако ее необходимо приблизительно изобразить многоугольником. Чем меньше заданная погрешность, тем из большего числа точек должен состоять многоугольник. Это увеличивает сложность результата, но уменьшает его погрешность.  
  
 *relative*  
 Значение типа **bit**, указывающее значение *tolerance*: относительное или абсолютное. Если задано значение TRUE или 1, то используется относительная погрешность, которая вычисляется как произведение параметра *tolerance* и диаметра ограничивающего прямоугольника экземпляра. Если этот аргумент имеет значение FALSE или 0, то погрешность является абсолютной, а значение *tolerance* задает максимальное абсолютное отклонение от идеальной буферной дистанции для возвращаемого линейного приближения.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 Параметр *tolerance* должен быть больше нуля. Если *tolerance* <= 0, вызывается исключение `System.ArgumentOutOfRangeException`.  
  
> [!NOTE]  
>  Так как параметр *tolerance* имеет тип **float**, то может возникнуть исключение `System.Runtime.InteropServices.COMException`, если значение, заданное в качестве погрешности, слишком мало, из-за особенностей округления типов с плавающей запятой.  
  
## <a name="remarks"></a>Remarks  
 Когда *distance* > 0, возвращается экземпляр **Polygon** или **MultiPolygon**.  
  
> [!NOTE]  
>  Так как аргумент distance относится к типу **float**, то в расчетах очень маленькое значение может быть приравнено к нулю. Когда это происходит, возвращается экземпляр **geometry**. См. статью [Типы данных float и real (Transact-SQL)](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Когда *distance* = 0, возвращается копия вызывающего экземпляра **geometry**.  
  
 Когда *distance* < 0, то  
  
-   возвращается пустой экземпляр **GeometryCollection**, если измерения экземпляра — 0 или 1.  
  
-   Возвращается отрицательный буфер, если измерений экземпляра 2 или более.  
  
    > [!NOTE]  
    >  Отрицательный буфер может также создать пустой экземпляр **GeometryCollection**.  
  
 Отрицательный буфер удаляет все точки на указанном расстоянии от границы экземпляра **geometry**.  
  
 Ошибкой между теоретическим и вычисляемым буфером является max(tolerance, extents \* 1.E-7), где погрешность является значением параметра *tolerance*. Дополнительные сведения об экстентах см. в статье [Справочник по методам типа данных geometry](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point`, а метод `BufferWithTolerance()` получает приблизительный буфер вокруг этого экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 3)', 0);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STBuffer (тип данных geometry)](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

