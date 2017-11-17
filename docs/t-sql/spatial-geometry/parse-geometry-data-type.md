---
title: "Parse (тип данных geometry) | Документы Microsoft"
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
dev_langs:
- TSQL
helpviewer_keywords:
- Parse (geometry Data Type)
ms.assetid: 6e080919-4b64-46cd-8dd2-254a9c232e53
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64adf9398a6ea63203f75714aa97ccf2653e947b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="parse-geometry-data-type"></a>Parse (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geometry** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT). `Parse()`эквивалентно [STGeomFromText()](../../t-sql/spatial-geometry/parse-geometry-data-type.md), за тем исключением, что он подразумевается пространственного идентификатор ссылки (SRID) 0 как параметр. Входные данные могут дополнительно содержать значения Z (высота) и M (мера).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parse ( 'geometry_tagged_text' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_tagged_text*  
 Является WKT-представление **geometry** экземпляр, который необходимо вернуть. *geometry_tagged_text* — **nvarchar** выражение.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Тип OGC **geometry** экземпляр, возвращаемый `Parse()` равно соответствующих входных данных WKT.  
  
 Строка «Null» будет интерпретироваться как строку null **geometry** экземпляра.  
  
 Этот метод вызывает исключение **FormatException** Если входные данные имеют неверный формат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Parse()` применяется для создания экземпляра `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Parse('LINESTRING (100 100, 20 180, 180 180)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STGeomFromText](../../t-sql/spatial-geometry/parse-geometry-data-type.md)   
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


