---
title: STGeomCollFromWKB (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomCollFromWKB (geometry Data Type)
- STGeomCollFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromWKB (geometry Data Type)
ms.assetid: 6c55032c-7f5e-4181-8e67-c0265032db63
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e5222f3076126f26a03d8634bff05f32ccd4b723
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53979790"
---
# <a name="stgeomcollfromwkb-geometry-data-type"></a>STGeomCollFromWKB (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geometrycollection** из WKB-представления консорциума OGC.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STGeomCollFromWKB ( 'WKB_geometrycollection' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *WKB_geometrycollection*  
 Представление в формате WKB возвращаемого экземпляра **geometrycollection**. *WKB_geometrycollection* — это выражение **varbinary(max)**.  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 В зависимости от соответствующих входных данных WKB типу OGC экземпляра **geometry**, возвращаемого `STGeomCollFromWKB()`, задается значение **GeomCollection**, **MultiPolygon**, **MultiLineString** или **MultiPoint**.  
  
 Этот метод вызывает исключение FormatException, если входные данные представлены в неверном формате.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере используется метод `STGeomCollFromWKB()`, чтобы создать экземпляр **geometry**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromWKB(0x0107000000020000000103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440010100000000000000000024400000000000002440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические геометрические методы OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

