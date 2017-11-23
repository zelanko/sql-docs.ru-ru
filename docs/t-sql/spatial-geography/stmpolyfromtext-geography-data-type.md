---
title: "STMPolyFromText (тип данных geography) | Документы Microsoft"
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
- STMPolyFromText (geography Data Type)
- STMPolyFromText_TSQL
dev_langs: TSQL
helpviewer_keywords: STMPolyFromText method
ms.assetid: 15356c0f-5144-418d-aa96-3e7ea5fecea3
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c7f569539d9105f93b7b95b4e7e10910fd90e7b8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stmpolyfromtext-geography-data-type"></a>STMPolyFromText (географический тип данных)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geography** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT), дополненное всеми значениями Z (уровень) и значения M (Мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STMPolyFromText ( 'multipolygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *multipolygon_tagged_text*  
 Является WKT-представление **geographyMultiPolygon** экземпляр, который необходимо вернуть. *multipolygon_tagged_text* — **nvarchar(max)** выражение.  
  
 *SRID*  
 — **Int** выражение, представляющее пространственной идентификатор ссылки (SRID) из **geographyMultiPolygon** экземпляр, который необходимо вернуть.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **Sql Geography**  
  
 Тип OGC: **MultiPolygon**  
  
## <a name="remarks"></a>Замечания  
 Этот метод создает исключение **FormatException** Если входные данные имеют неверный формат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STMPolyFromText()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STMPolyFromText('MULTIPOLYGON(((-122.358 47.653, -122.348 47.649, -122.358 47.658, -122.358 47.653)), ((-122.341 47.656, -122.341 47.661, -122.351 47.661, -122.341 47.656)))', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические географические методы OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
