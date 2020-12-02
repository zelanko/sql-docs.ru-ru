---
description: STBuffer (тип данных geography)
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
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 1d39e58c6dd4fa648d8d4118414925777eb3535b
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "92038323"
---
# <a name="stbuffer-geography-data-type"></a>STBuffer (тип данных geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает географический объект, представленный объединением всех точек, расстояние которых от экземпляра **geography** меньше или равно указанному значению.  
  
 Этот метод типа данных geography поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STBuffer ( distance )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *distance*  
 Значение типа **float** (**double** в .NET Framework), указывающее расстояние от объекта **geography**, вокруг которого вычисляется буфер.  
  
 Максимальное расстояние при вычислении буфера не может превышать 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 окружности Земли) или полную окружность Земли.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Метод STBuffer() вычисляет буфер аналогично методам [BufferWithTolerance](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md), задавая аргументы *tolerance* = abs(distance) \* 0,001 и *relative* = **false**.  
  
 Отрицательный буфер удаляет все точки в пределах заданного расстояния от границы экземпляра **geography**.  
  
 `STBuffer()` возвращает экземпляр **FullGlobe** в определенных случаях; например, `STBuffer()` возвращает экземпляр **FullGlobe**, если буферное расстояние больше, чем расстояние от экватора до полюса. Буфер не может превышать по размеру полный шар.  
  
 Этот метод вызовет исключение **ArgumentException** в тех экземплярах **FullGlobe**, где расстояние буфера превышает следующее ограничение:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 окружности Земли)  
  
 Ограничение максимального расстояние позволяет конструкции буфера быть как можно более гибкой.  
  
 Ошибкой между теоретическим и вычисляемым буфером является max(tolerance, extents * 1.E-7), где tolerance = distance \* 0,001. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geography](./stequals-geography-data-type.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString``geography`. Затем используется метод `STBuffer()`, чтобы возвратить область в пределах 1 метра от экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STBuffer(1).ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [BufferWithTolerance (тип данных geography)](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)   
 [Методы OGC, применяемые к географическим объектам](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
