---
title: STEndpoint (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEndpoint (geometry Data Type)
- STEndpoint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STEndpoint (geometry Data Type)
ms.assetid: 61773c45-b568-4e0c-94da-1310c42de7f5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2fcdb5b59b146f55a1b83de8e26a4bf356255bf1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750292"
---
# <a name="stendpoint-geometry-data-type"></a>STEndpoint (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает конечную точку экземпляра **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STEndPoint ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
 Тип открытого геопространственного консорциума (OGC): **Point**  
  
## <a name="remarks"></a>Remarks  
 Метод `STEndPoint()` эквивалентен методу [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md) (x.NumPoints()).  
  
 Если этот метод вызывается для пустого экземпляра **geometry**, то он возвращает значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере с помощью метода `LineString` создается экземпляр `STGeomFromText()`, а затем метод `STEndpoint()` производит получение конечной точки экземпляра `LineString`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STEndPoint().ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

