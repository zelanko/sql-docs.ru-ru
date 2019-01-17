---
title: STBuffer (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBuffer (geography Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geography Data Type)
ms.assetid: cb4deab8-642b-44d9-b3d9-85114d64021e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 55316e61b2690e56949e7fff3fe209e9b02fa0aa
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53979310"
---
# <a name="stbuffer-geography-data-type"></a>STBuffer (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает географический объект, представленный объединением всех точек, расстояние которых от экземпляра **geography** меньше или равно указанному значению.  
  
 Этот метод типа данных geography поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *distance*  
 Значение типа **float** (**double** в .NET Framework), указывающее расстояние от объекта **geography**, вокруг которого вычисляется буфер.  
  
 Максимальное расстояние при вычислении буфера не может превышать 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 окружности Земли) или полную окружность Земли.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Метод STBuffer() вычисляет буфер аналогично методам [BufferWithTolerance](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md), задавая аргументы *tolerance* = abs(distance) \* 0,001 и *relative* = **false**.  
  
 Отрицательный буфер удаляет все точки в пределах заданного расстояния от границы экземпляра **geography**.  
  
 `STBuffer()` возвращает экземпляр **FullGlobe** в определенных случаях; например, `STBuffer()` возвращает экземпляр **FullGlobe**, если буферное расстояние больше, чем расстояние от экватора до полюса. Буфер не может превышать по размеру полный шар.  
  
 Этот метод вызовет исключение **ArgumentException** в тех экземплярах **FullGlobe**, где расстояние буфера превышает следующее ограничение:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 окружности Земли)  
  
 Ограничение максимального расстояние позволяет конструкции буфера быть как можно более гибкой.  
  
 Ошибкой между теоретическим и вычисляемым буфером является max(tolerance, extents * 1.E-7), где tolerance = distance \* 0,001. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geography](https://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString``geography`. Затем используется метод `STBuffer()`, чтобы возвратить область в пределах 1 метра от экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STBuffer(1).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [BufferWithTolerance (тип данных geography)](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)   
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
