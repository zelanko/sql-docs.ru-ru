---
title: "ToString (тип данных geometry) | Документы Microsoft"
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
f1_keywords: ToString (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 06bf05558bfefdf679d479429f5e71afcfcb7c6b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="tostring-geometry-data-type"></a>ToString (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает представление WKT консорциума OGC геометрического объекта, дополненного всеми значениями Z (уровень) и M (мера) этого экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **nvarchar(max)**  
  
 Возвращаемый тип CLR: **SqlString**  
  
## <a name="remarks"></a>Замечания  
 Этот метод возвращает строку «Null», если он вызван для неопределенного экземпляра.  
  
 Вызов этого метода по отношению к определенным экземплярам эквивалентен использованию метода `AsTextZM().`  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `LineString` и с помощью `ToString()` для выборки текстового описания экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STAsText &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

