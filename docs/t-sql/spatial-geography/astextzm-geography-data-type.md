---
title: "AsTextZM (тип данных geography) | Документы Microsoft"
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
f1_keywords:
- AsTextZM (geography Data Type)
- AsTextZM_TSQL
- AsTextZM
- AsTextZM_(geography_Data_Type)_TSQL
dev_langs: TSQL
helpviewer_keywords: AsTextZM method
ms.assetid: e9dc27f6-e945-4457-8498-7644db34008e
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95a5af7ee424ddc4413c41aa16404c0491adff4c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="astextzm-geography-data-type"></a>AsTextZM (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает представление Open Geospatial Consortium (OGC) Well-Known Text (WKT) **geography** экземпляр дополненного **Z** (высота) и **M** (Мера) значения, сопровождающих экземпляр.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **nvarchar(max)**  
  
 Возвращаемый тип CLR: **SqlChars**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `Point` экземпляру, содержащему **Z** (высота) и **M** значений (мер). `STAsText()`Выбирает значения WKT (– 122,34900 47,65100); `AsTextZM()` выбирает те же значения WKT, а также возвращает значения для **Z** и **M**, давая в результате (– 122,34900 47,65100 10,3 12).  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [М &#40; тип данных geography &#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Я &#40; тип данных geography &#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
