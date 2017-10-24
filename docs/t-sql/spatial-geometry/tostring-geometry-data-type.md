---
title: "ToString (тип данных geometry) | Документы Microsoft"
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
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ffe70ad712605222a66dc12ba7af4e330dc12c9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="tostring-geometry-data-type"></a>ToString (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
  
  


