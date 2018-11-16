---
title: AsGml (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8d3b518f9255f3a6ed08bc66fdbd43eba6ed1472
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699752"
---
# <a name="asgml-geometry-data-type"></a>AsGml (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает представление экземпляра **geometry** на языке GML.
  
Дополнительные сведения о языке GML см. в следующей спецификации открытого геопространственного консорциума (OGC): [Спецификации OGC, язык GML](https://go.microsoft.com/fwlink/?LinkId=93629).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **xml**  
  
 Тип возвращаемых данных CLR: **SqlXml**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` а метод `AsGML()` производит получение его описания на языке GML.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0)  
SELECT @g.AsGml();  
```  
  
 Этот метод возвращает описание в виде экземпляра `LineString`.  
  
```  
<LineString xmlns="https://www.opengis.net/gml">  
<posList>0 0 0 1 1 0</posList></LineString>  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

