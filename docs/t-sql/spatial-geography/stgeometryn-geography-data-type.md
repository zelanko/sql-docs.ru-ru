---
title: "STGeometryN (тип данных geography) | Документы Microsoft"
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
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5d11dc77ce692543068cba6739ef982bc8264c8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает заданное **geography** элемент в **GeometryCollection** или один из его подтипов. При использовании применительно к подтипу STGeometryN() **GeometryCollection**, такие как **MultiPoint** или **MultiLineString**, этот метод возвращает **geography**  экземпляра при вызове с N = 1.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — **Int** выражение между 1 и число **geography** экземпляров в **GeometryCollection**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Этот метод возвращает значение null, если параметр больше, чем результат [STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md) и вызывает **ArgumentOutOfRangeException** Если *выражение* аргумент принимает значение меньше 1.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `MultiPoint``geography` и с помощью `STGeometryN()` для поиска второго `geography` экземпляр **GeometryCollection**.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
