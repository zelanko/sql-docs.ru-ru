---
title: STGeometryType (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryType_TSQL
- STGeometryType (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType (geometry Data Type)
ms.assetid: 224cdc83-aa83-4ad4-bb82-b7481031e910
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c91ae4decb540d80e371153504121ee22bf3ccc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663462"
---
# <a name="stgeometrytype-geometry-data-type"></a>STGeometryType (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает имя типа открытого геопространственного консорциума (OGC), представленное экземпляром **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STGeometryType ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **nvarchar(4000)**  
  
 Тип возвращаемых данных CLR: **SqlString**  
  
## <a name="remarks"></a>Remarks  
 Имена типов OGC, которые могут быть возвращены `STGeometryType()`: **Point**, **LineString**, **CircularString**, **CompoundCurve**, **Polygon, CurvePolygon**, **GeometryCollection**, **MultiPoint**, **MultiLineString** и **MultiPolygon**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Polygon` и используется метод `STGeometryType()`, чтобы проверить, является ли этот экземпляр многоугольником.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 0);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

