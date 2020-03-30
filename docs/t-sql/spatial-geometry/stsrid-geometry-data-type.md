---
title: STSrid (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geometry Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid (geometry Data Type)
ms.assetid: 5e0de983-a0fe-48b7-9e08-30588d7271e2
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f1119c0c906e3a3825882e3fe1043e9bdaceb0f9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68066302"
---
# <a name="stsrid-geometry-data-type"></a>STSrid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** является целым числом, представляющим собой идентификатор пространственной ссылки экземпляра.  
  
Это свойство можно изменять.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STSrid  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип CLR: **SqlInt32**  
  
## <a name="examples"></a>Примеры  
 В первом примере создается экземпляр **geometry** со значением SRID, равным 13, и используется метод `STSrid` для подтверждения SRID.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 13);  
SELECT @g.STSrid;  
```  
  
 Во втором примере с помощью метода `STSrid` значение SRID экземпляра изменяется на 23, а затем подтверждается измененное значение SRID.  
  
```  
SET @g.STSrid = 23;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>См. также:  
 [STX (тип данных geometry)](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY (тип данных geometry)](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

