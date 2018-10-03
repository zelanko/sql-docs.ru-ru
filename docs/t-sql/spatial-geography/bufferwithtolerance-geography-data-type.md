---
title: BufferWithTolerance (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e5d184b502fc3c1bac1eff8201d43bbe22d93aad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766702"
---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает геометрический объект, представляющий объединение всех точек, расстояние от которых до заданного экземпляра **geography** не превышает заданного значения с указанной погрешностью.  
  
 Этот метод типа данных geography поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Аргументы  
 *distance*  
 Это выражение типа **float** задает расстояние от экземпляра **geography**, для которого вычисляется буфер.  
  
 Максимальное расстояние при вычислении буфера не может превышать 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 окружности Земли) или полную окружность Земли.  
  
 *tolerance*  
 Выражение типа **float**, задающее погрешность буферного расстояния.  
  
 Значение *tolerance* относится к максимальному отклонению в идеальном буферном расстоянии для возвращенной линейной аппроксимации.  
  
 Например, идеальной границей буфера для точки является окружность, однако ее необходимо приблизительно изобразить многоугольником. Чем меньше заданная погрешность, тем из большего числа точек должен состоять многоугольник. Это увеличивает сложность результата, но уменьшает его погрешность.  
  
 Минимальный предел составляет 0,1 % от расстояния, и любая меньшая погрешность будет округлена до этого значения.  
  
 *relative*  
 Значение типа **bit**, указывающее значение *tolerance*: относительное или абсолютное. Если задано значение TRUE или 1, то используется относительная погрешность, которая вычисляется как произведение параметра *tolerance* и углового фактора \* экваториальный радиус эллипсоида. Если этот аргумент имеет значение FALSE или 0, то погрешность является абсолютной, а значение *tolerance* задает максимальное абсолютное отклонение от идеальной буферной дистанции для возвращаемого линейного приближения.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывает исключение **ArgumentException**, если *distance* не является числом (NAN) или если *distance* равно плюс/минус бесконечности.  Этот метод также вызывает исключение **ArgumentException**, если *tolerance* равно нулю (0), не является числом (NAN), отрицательным или равно плюс/минус бесконечности.  
  
 `STBuffer()` возвращает экземпляр **FullGlobe** в определенных случаях; например, `STBuffer()` возвращает экземпляр **FullGlobe** для двух полюсов, если буферное расстояние больше, чем расстояние от экватора до полюса.  
  
 Этот метод вызовет исключение **ArgumentException** в тех экземплярах **FullGlobe**, где расстояние буфера превышает следующее ограничение:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 окружности Земли)  
  
 Ошибкой между теоретическим и вычисляемым буфером является max(tolerance, extents \* 1.E-7), где погрешность является значением параметра *tolerance*. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point`, а метод `BufferWithTolerance()` получает приблизительный буфер вокруг этого экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [STBuffer (тип данных geography)](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
