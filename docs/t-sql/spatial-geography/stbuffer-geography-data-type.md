---
title: "STBuffer (тип данных geography) | Документы Microsoft"
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
- STBuffer (geography Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geography Data Type)
ms.assetid: cb4deab8-642b-44d9-b3d9-85114d64021e
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2fa06f270ad653e9c8e43a5ec5456257e785670e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stbuffer-geography-data-type"></a>STBuffer (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает географический объект, представляющий объединение всех точек, расстояние которых от **geography** экземпляр меньше или равно указанному значению.  
  
 Это geography, тип данных поддерживает метод **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *расстояние*  
 Значение типа **float** (**двойные** в платформе .NET Framework) указывающее расстояние от **geography** , вокруг которого вычисляется буфер.  
  
 Максимальное расстояние буфера не может превышать 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* 1/2 окружности Земли) или полного земного шара.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Вычисляет буфер аналогично STBuffer() [BufferWithTolerance](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md), указав *отклонения* = abs(distance) \* .001 и *относительный*  =  **false**.  
  
 Отрицательный буфер удаляет все точки в пределах заданного расстояния от границы **geography** экземпляра.  
  
 `STBuffer()`Возвращает **FullGlobe** экземпляра в определенных случаях; например, `STBuffer()` возвращает **FullGlobe** экземпляра, когда буферное расстояние больше, чем расстояние от экватора до полюса. Буфер не может превышать по размеру полный шар.  
  
 Этот метод вызывает исключение **ArgumentException** в **FullGlobe** экземпляров, где расстояние буфера превышает следующее ограничение:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* 1/2 окружности Земли)  
  
 Ограничение максимального расстояние позволяет конструкции буфера быть как можно более гибкой.  
  
 Ошибкой между теоретическим и рассчитанным буфером является max (погрешность, экстентов * 1.E-7) где отклонение = distance \* .001. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `LineString``geography` экземпляра. Затем используется метод `STBuffer()`, чтобы возвратить область в пределах 1 метра от экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STBuffer(1).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [BufferWithTolerance &#40; тип данных geography &#41;](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)   
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

