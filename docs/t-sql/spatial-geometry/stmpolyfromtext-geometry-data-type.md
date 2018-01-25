---
title: "STMPolyFromText (тип данных geometry) | Документы Microsoft"
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
- STMPolyFromText (geometry Data Type)
- STMPolyFromText_TSQL
dev_langs: TSQL
helpviewer_keywords: STMPolyFromText (geometry Data Type)
ms.assetid: f087a61c-f063-4fb8-8f1c-251a2fed76a1
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9b4610481d315122b2d811ef30e65b1d30a1f4d5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stmpolyfromtext-geometry-data-type"></a>STMPolyFromText (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geometry** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT) с Z (высота) и значения M (Мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STMPolyFromText ( 'multipolygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *multipolygon_tagged_text*  
 Является WKT-представление **geometryMultiPolygon** экземпляр, который необходимо вернуть. *multipolygon_tagged_text* — **nvarchar(max)** выражение.  
  
 *SRID*  
 — **Int** выражение, представляющее пространственной идентификатор ссылки (SRID) из **geometryMultiPolygon** экземпляр, который необходимо вернуть.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **Sql Geometry**  
  
 Тип OGC: **MultiPolygon**  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывает исключение **FormatException** Если входные данные имеют неверный формат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STMPolyFromText()` применяется для создания экземпляра `geometry`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPolyFromText('MULTIPOLYGON (((5 5, 10 5, 10 10, 5 5)), ((10 10, 100 10, 200 200, 30 30, 10 10)))', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Статические геометрические методы OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

