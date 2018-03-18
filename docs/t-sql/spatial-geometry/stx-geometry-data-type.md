---
title: "STX (тип данных geometry) | Документы Майкрософт"
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2dacaadae631735c64a0882f4cc90c7dd16fd6e7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stx-geometry-data-type"></a>STX (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Свойство координаты по оси X экземпляра **Point**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STX  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Это свойство будет иметь значение NULL, если экземпляр **geometry** не является точкой.  
  
 Это свойство доступно только для чтения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` и с помощью метода `STX` получается координата экземпляра по оси X.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STX;  
```  
  
## <a name="see-also"></a>См. также:  
 [STY (тип данных geometry)](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [STSrid (тип данных geometry)](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

