---
title: "STPolyFromText (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STPolyFromText_TSQL
- STPolyFromText (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STPolyFromText (geometry Data Type)
ms.assetid: a7c1c9f0-1dd5-493b-b206-83bbfa33452b
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0edae0af8499c783ef20b412dab9ee6422d8cfd1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stpolyfromtext-geometry-data-type"></a>STPolyFromText (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geometry** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT), дополненное всеми значениями Z (уровень) и значения M (Мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STPolyFromText ( 'polygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *polygon_tagged_text*  
 Является WKT-представление **geometryPolygon** экземпляр, который необходимо вернуть. *polygon_tagged_text* — **nvarchar(max)** выражение.  
  
 *SRID*  
 — **Int** выражение, представляющее пространственной идентификатор ссылки (SRID) из **geometryPolygon** экземпляр, который необходимо вернуть.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
 Тип OGC: **многоугольника**  
  
## <a name="remarks"></a>Замечания  
 Этот метод вызывает исключение **FormatException** Если входные данные имеют неверный формат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STPolyFromText()` применяется для создания экземпляра `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPolyFromText('POLYGON ((5 5, 10 5, 10 10, 5 5))', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические геометрические методы OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

