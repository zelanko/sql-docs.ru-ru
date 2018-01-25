---
title: "STPointN (тип данных geography) | Документы Microsoft"
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
- STPointN_TSQL
- STPointN (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STPointN method
ms.assetid: 47670feb-b9e0-4b4b-af83-b9bba7da66ac
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26a3974bfb122bcd44de25ba1a82cae6caba7e9b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stpointn-geography-data-type"></a>STPointN (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает указанную точку в **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — **Int** выражение от 1 до количества точек в **geography** экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
 Открытый тип Geospatial Consortium (OGC): **точки**  
  
## <a name="remarks"></a>Remarks  
 Если **geography** экземпляра, созданные пользователем, STPointN() возвращает точку, указанную *выражение* путем упорядочения точек в том порядке, в котором они были первоначально введены.  
  
 Если **geography** создан системой, STPointN() возвращает точку, указанную *выражение* путем упорядочения всех точек в том же порядке, они должны быть выведены: сначала по  **География** экземпляра, затем по кольцу в пределах экземпляра (если применимо), а затем по точкам внутри кольца. Это порядок является детерминированным.  
  
 Если этот метод вызывается со значением менее 1, он выдает **ArgumentOutOfRangeException**.  
  
 Если этот метод вызывается со значением, превышающим число точек в экземпляре, он возвращает значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString`, и при помощи метода `STPointN()` производится получение второй точки в его описании.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
