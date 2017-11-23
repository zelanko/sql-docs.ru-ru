---
title: "STMLineFromText (тип данных geography) | Документы Microsoft"
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
- STMLineFromText (geography Data Type)
- STMLineFromText_TSQL
dev_langs: TSQL
helpviewer_keywords: STLineFromText method
ms.assetid: 66dfd722-a9bd-45d3-9788-f1946dd23e17
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f64223420ea81247e4e8456614fe2e9b8b30f05
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stmlinefromtext-geography-data-type"></a>STMLineFromText (географический тип данных)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geography** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT), дополненное всеми значениями Z (уровень) и значения M (Мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STMLineFromText ( 'multilinestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *multilinestring_tagged_text*  
 Является WKT-представление **geographyMultiLineString** экземпляр, который необходимо вернуть. *multilinestring_tagged_text* — **nvarchar(max)** выражение.  
  
 *SRID*  
 — **Int** выражение, представляющее пространственной идентификатор ссылки (SRID) из **geographyMultiLineString** экземпляр, который необходимо вернуть.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
 Тип OGC: **MultiLineString**  
  
## <a name="remarks"></a>Замечания  
 Этот метод создает исключение **FormatException** Если входные данные имеют неверный формат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STMLineFromText()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STMLineFromText('MULTILINESTRING ((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические географические методы OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
