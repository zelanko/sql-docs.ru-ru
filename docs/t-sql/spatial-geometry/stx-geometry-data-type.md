---
title: "STX (тип данных geometry) | Документы Microsoft"
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
- STX (geometry Data Type)
- STX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STX (geometry Data Type)
ms.assetid: 2aef77e8-0460-43f9-bad6-2aae6d8c36f9
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3cfed425a18babe80de7522f9adec3718d6fdf19
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stx-geometry-data-type"></a>STX (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Свойство координаты X **точки**экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STX  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип: **число с плавающей запятой**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 Значение этого свойства будет иметь значение null, если **geometry** экземпляр не является точкой.  
  
 Это свойство предназначено только для чтения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` и с помощью метода `STX` получается координата экземпляра по оси X.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STX;  
```  
  
## <a name="see-also"></a>См. также:  
 [STY (тип данных geometry)](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [STSrid &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


