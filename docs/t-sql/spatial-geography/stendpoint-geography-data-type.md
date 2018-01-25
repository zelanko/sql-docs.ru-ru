---
title: "STEndpoint (тип данных geography) | Документы Microsoft"
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
- STEndpoint (geography Data Type)
- STEndpoint_TSQL
dev_langs: TSQL
helpviewer_keywords: STEndpoint method
ms.assetid: 8974cd07-8ec4-4126-8fc2-fdcf322ccedd
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 910e11dc72d4bb0ec7a2d09a0217c4b9d7c12431
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stendpoint-geography-data-type"></a>STEndpoint (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает конечную точку **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STEndPoint ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
 Открытый тип Geospatial Consortium (OGC): **точки**  
  
## <a name="remarks"></a>Remarks  
 Эквивалентно STEndPoint() [STPointN](../../t-sql/spatial-geography/stpointn-geography-data-type.md)`(x.STNumPoints``())`.  
  
 Этот метод возвращает значение null, если вызван с пустым **geography** экземпляра.  
  
## <a name="examples"></a>Примеры  
 В следующем примере с помощью метода `LineString` создается экземпляр `STGeomFromText()`, а затем метод `STEndpoint()` производит получение конечной точки экземпляра `LineString`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STEndPoint().ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
