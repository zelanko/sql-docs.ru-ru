---
title: "Parse (тип данных geography) | Документы Microsoft"
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
dev_langs: TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 932a65d59e0083463533493071987f6af79be54c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="parse-geography-data-type"></a>Parse (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **geography** экземпляр из представления Open Geospatial Consortium (OGC) Well-Known Text (WKT). Эквивалентно Parse() [STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md), за исключением того, что предполагается идентификатор пространственной ссылки (SRID) 4326 как параметр. Входные данные могут дополнительно содержать значения Z (высота) и M (мера).
  
Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_tagged_text*  
 Является WKT-представление **geography** возвращаемого экземпляра. *geography_tagged_text* — **nvarchar** выражение.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Тип OGC **geography** экземпляр, возвращаемый `Parse()` равно соответствующих входных данных WKT.  
  
 Строка «Null» будет интерпретироваться как строку null **geography** экземпляра.  
  
 Этот метод вызывает исключение **ArgumentException** Если вход содержит противоположную границу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Parse()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические географические методы](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText (тип данных geography)](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
