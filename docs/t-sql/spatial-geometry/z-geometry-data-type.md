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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Z (geometry Data Type)
- Z_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z (geometry Data Type)
ms.assetid: a62ed736-44df-4591-9109-ce90e1df9bd3
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad6d857cb2028c34e6c1d1e9200537fbcd007989
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

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
  
  


