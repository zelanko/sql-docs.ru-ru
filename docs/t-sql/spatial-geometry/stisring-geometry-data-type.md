---
title: STIsRing (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STIsRing_TSQL
- STIsRing (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsRing (geometry Data Type)
ms.assetid: ea0063be-1c74-4cc4-ac6f-b65321ddfa54
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e555e7044539208043dc4195edb619a31baec94e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33063031"
---
# <a name="stisring-geometry-data-type"></a>STIsRing (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает 1, если экземпляр **geometry** соответствует указанным ниже требованиям.
-   Является экземпляром **LineString**.  
-   Он закрыт.  
-   Он является простым.  
-   Возвращает значение 0, если экземпляр **LineString** не соответствует требованиям.  

 Чтобы экземпляр **geometry** был замкнутым и простым, как функция [STIsClosed()](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md), так и функция [STIsSimple()](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md) должны возвращать значение 1 при вызове для экземпляра. Для определения типа экземпляра **geometry** используйте функцию [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsRing ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает значение NULL, если экземпляр не является **LineString**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и используется метод `STIsRing()`, чтобы проверить, что экземпляр является кольцом.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0, 0 0)', 0);  
SELECT @g.STIsRing();  
```  
  
## <a name="see-also"></a>См. также:  
 [STIsClosed (тип данных geometry)](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STGeometryType (тип данных geometry)](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [STIsSimple (тип данных geometry)](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

