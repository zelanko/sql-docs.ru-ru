---
title: "AsGml (тип данных geometry) | Документы Microsoft"
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
- AsGml(geometry_Data_Type)_TSQL
- AsGml
- AsGml(geometry Data Type)
- AsGml_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml (geometry Data Type)
ms.assetid: f6c2e130-05f3-4ef3-921b-d78b51437d48
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a4ca0fcd5b8b7b4ffdb39d3201f7060efe18a74
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="asgml-geometry-data-type"></a>AsGml (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
  
  


