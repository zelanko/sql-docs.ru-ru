---
title: Parse (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse (geometry Data Type)
ms.assetid: 6e080919-4b64-46cd-8dd2-254a9c232e53
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: a856bc8e5ea9a3c125e3d353963d5fcdf5b8492a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937448"
---
# <a name="parse-geometry-data-type"></a>Parse (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geometry** из WKT-представления открытого геопространственного консорциума (OGC). Метод `Parse()` эквивалентен методу [STGeomFromText()](../../t-sql/spatial-geometry/parse-geometry-data-type.md) за исключением того, что ожидает в качестве параметра идентификатор пространственной ссылки (SRID) со значением 0. Входные данные могут дополнительно содержать значения Z (высота) и M (мера).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parse ( 'geometry_tagged_text' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_tagged_text*  
 WKT-представление возвращаемого экземпляра **geometry**. *geometry_tagged_text* является выражением типа **nvarchar**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Тип OGC экземпляра **geometry**, возвращаемый методом `Parse()`, получает значение в зависимости от соответствующих входных данных WKT.  
  
 Строка "Null" будет интерпретирована как экземпляр **geometry** со значением NULL.  
  
 Этот метод вызывает исключение **FormatException**, если входные данные представлены в неверном формате.  
  
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
  
  

