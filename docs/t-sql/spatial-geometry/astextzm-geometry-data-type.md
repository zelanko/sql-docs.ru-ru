---
title: "AsTextZM (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsTextZM_TSQL
- AsTextZM
- AsTextZM (geometry Data Type)
- AsTextZM_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM (geometry Data Type)
ms.assetid: 08ac8aa0-aff7-4b22-87e0-1a1d55dcbc04
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 91f77bd684d79bbef2530307aa65fc0d92b91c5e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="astextzm-geometry-data-type"></a>AsTextZM (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает представление Open Geospatial Consortium (OGC) Well-Known Text (WKT) экземпляра геометрического объекта, дополненного **Z** (высота) и **M** значения (Мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **nvarchar(max)**  
  
 Возвращаемый тип CLR: **SqlChars**  
  
## <a name="remarks"></a>Замечания  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `Point` экземпляру, содержащему **Z** (высота) и **M** значений (мер). `STAsText()`Выбирает значения WKT (1, 2); `AsTextZM()` выбирает те же значения WKT, а также возвращает значения для **Z** и **M**, возвращая (1 2 3 4).  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [М &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Я &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  


