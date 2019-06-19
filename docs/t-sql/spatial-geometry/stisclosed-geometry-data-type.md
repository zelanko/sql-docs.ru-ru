---
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
manager: craigg
ms.openlocfilehash: 1212beb7f65789ec986c45af1d1a2b2c3eb8d83f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938830"
---
# <a name="stisclosed-geometry-data-type"></a>STIsClosed (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение 1, если начальная и конечная точки заданного экземпляра **geometry** совпадают. Возвращает значение 1 для типов коллекции **geometrycollection**, если каждый содержащийся в ней экземпляр **geometry** является замкнутым. Возвращает значение 0, если экземпляр является незамкнутым.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемого значения CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает значение 0, если среди фигур экземпляра **geometry** есть точки или экземпляр является пустым.  
  
 Все экземпляры **Polygon** считаются замкнутыми.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и вызывается метод `STIsClosed()`, который определяет, является ли экземпляр `LineString` замкнутым.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

