---
title: "Parse (тип данных geography) | Документы Майкрософт"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c29c43af7034f86fa993fc5f12046200216ec57f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="parse-geography-data-type"></a>Parse (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geography** из WKT-представления консорциума OGC. Функция Parse() эквивалентна функции [STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md), за исключением того, что ожидает в качестве параметра идентификатор пространственной ссылки (SRID) значение 4326. Входные данные могут дополнительно содержать значения Z (высота) и M (мера).
  
Этот метод типа данных **geography** поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_tagged_text*  
 WKT-представление возвращаемого экземпляра **geography**. *geography_tagged_text* является выражением типа **nvarchar**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Примечания  
 Тип OGC экземпляра **geography**, возвращаемый методом `Parse()`, получает значение в зависимости от соответствующих входных данных WKT.  
  
 Строка "Null" будет интерпретирована как экземпляр **geography** со значением NULL.  
  
 Этот метод вызывает исключение **ArgumentException**, если входные данные содержат противоположную границу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Parse()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные статические географические методы](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText (тип данных geography)](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
