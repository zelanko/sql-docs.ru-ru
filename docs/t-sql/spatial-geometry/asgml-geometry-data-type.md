---
title: "AsGml (тип данных geometry) | Документы Microsoft"
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
- AsGml(geometry_Data_Type)_TSQL
- AsGml
- AsGml(geometry Data Type)
- AsGml_TSQL
dev_langs: TSQL
helpviewer_keywords: AsGml (geometry Data Type)
ms.assetid: f6c2e130-05f3-4ef3-921b-d78b51437d48
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e845650e0ecfe2fa71fe94dbe81a8a672abd3e10
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="asgml-geometry-data-type"></a>AsGml (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает представление языка разметки Geography (GML) **geometry** экземпляра.
  
Дополнительные сведения о языке GML см. в разделе следующей спецификации консорциума Ogc:[спецификации OGC, географический язык разметки.](http://go.microsoft.com/fwlink/?LinkId=93629)
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **xml**  
  
 Возвращаемый тип CLR: **SqlXml**  
  
## <a name="remarks"></a>Замечания  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` а метод `AsGML()` производит получение его описания на языке GML.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0)  
SELECT @g.AsGml();  
```  
  
 Этот метод возвращает описание в виде экземпляра `LineString`.  
  
```  
<LineString xmlns="http://www.opengis.net/gml">  
<posList>0 0 0 1 1 0</posList></LineString>  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

