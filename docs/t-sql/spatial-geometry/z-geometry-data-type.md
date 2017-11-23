---
title: "Z (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Z (geometry Data Type)
- Z_(geometry_Data_Type)_TSQL
dev_langs: TSQL
helpviewer_keywords: Z (geometry Data Type)
ms.assetid: a62ed736-44df-4591-9109-ce90e1df9bd3
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f39b62651d74fb97964a3e848ca857d33c9c3e94
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="z-geometry-data-type"></a>Z (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Значение Z (высота) экземпляра. Семантика значения высоты определяется пользователем.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип: **число с плавающей запятой**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 Значение этого свойства будет иметь значение null, если экземпляр geometry не является точкой, а также для любого **точки** экземпляра, для которой не установлено.  
  
 Это свойство предназначено только для чтения.  
  
 Координаты по оси Z не используются ни в каких вычислениях, выполненных библиотекой, и не проходят ни через какие библиотечные изменения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` со значениями Z (высота) и M (мера) и методом `Z` производится получение для него значения Z.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>См. также:  
 [М &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [AsTextZM &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

