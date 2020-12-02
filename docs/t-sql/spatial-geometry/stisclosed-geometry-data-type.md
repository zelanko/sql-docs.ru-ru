---
description: STIsClosed (тип данных geometry)
title: STIsClosed (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsClosed_TSQL
- STIsClosed (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed (geometry Data Type)
ms.assetid: 14edbb22-df7b-4b8a-b16c-ac477a5d32c1
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c92d311ba67c71f77fef8052bcfe8e5938d1f1b5
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88445046"
---
# <a name="stisclosed-geometry-data-type"></a>STIsClosed (тип данных geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает значение 1, если начальная и конечная точки заданного экземпляра **geometry** совпадают. Возвращает значение 1 для типов коллекции **geometrycollection**, если каждый содержащийся в ней экземпляр **geometry** является замкнутым. Возвращает значение 0, если экземпляр является незамкнутым.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsClosed ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Комментарии  
 Этот метод возвращает значение 0, если среди фигур экземпляра **geometry** есть точки или экземпляр является пустым.  
  
 Все экземпляры **Polygon** считаются замкнутыми.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и вызывается метод `STIsClosed()`, который определяет, является ли экземпляр `LineString` замкнутым.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

