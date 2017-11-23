---
title: "STGeometryN (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: STGeometryN (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f0f9249552ae3c69a3dd51a7070d0f17df79c483
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
