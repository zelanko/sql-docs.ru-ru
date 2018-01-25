---
title: "STGeomFromText (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 07/30/2017
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
- STGeomFromText (geography Data Type)
- STGeomFromText_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full globe
- STGeomFromText method
ms.assetid: 3717987b-77d8-4ccf-a1db-5a8016ac1083
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 43e9f3cf895645fade0ab5147972e1f0f773e1e8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stgeomfromtext-geography-data-type"></a>STGeomFromText (географический тип данных)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geography** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT), дополненное всеми значениями Z (уровень) и значения M (Мера), сопровождающими экземпляр.
  
Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STGeomFromText ( 'geography_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_tagged_text*  
 Является WKT-представление **geography** возвращаемого экземпляра. *geography_tagged_text* — **nvarchar(max)** выражение.  
  
 *SRID*  
 — **Int** выражение, представляющее пространственной идентификатор ссылки (SRID) из **geography** возвращаемого экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Тип OGC **geography** экземпляр, возвращаемый STGeomFromText() равно соответствующих входных данных WKT.  
  
 Этот метод вызывает исключение **ArgumentException** Если вход содержит противоположную границу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STGeomFromText()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Статические географические методы OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
