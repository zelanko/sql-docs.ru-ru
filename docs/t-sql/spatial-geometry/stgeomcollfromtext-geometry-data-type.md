---
title: "STGeomCollFromText (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeomCollFromText_TSQL
- STGeomCollFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText (geometry Data Type)
ms.assetid: 19e757b3-cb2e-4852-87b9-40a815ab707e
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 10c21174dfb176dd08ae30e4752b2f8ecfaa98f5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stgeomcollfromtext-geometry-data-type"></a>STGeomCollFromText (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geometry** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT), дополненное всеми значениями Z (уровень) и значения M (Мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometrycollection_tagged_text*  
 Является WKT-представление **geometry** экземпляр, который необходимо вернуть. *geometry_tagged_text* — **nvarchar(max)** выражение.  
  
 *SRID*  
 — **Int** выражение, представляющее пространственной идентификатор ссылки (SRID) из **geometry** экземпляр, который необходимо вернуть.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Тип OGC **geometry** экземпляр, возвращаемый `STGeomCollFromText()` равно соответствующих входных данных WKT.  
  
 Этот метод вызывает исключение, если входные данные не являются допустимыми.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется метод `STGeomCollFromText()`, чтобы создать геометрический объект.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION ( POLYGON((5 5, 10 5, 10 10, 5 5)), POINT(10 10) )', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические геометрические методы OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  


