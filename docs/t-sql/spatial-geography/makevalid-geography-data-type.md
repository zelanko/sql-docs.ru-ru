---
title: "MakeValid (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords: MakeValid method (geography)
ms.assetid: f67038e3-4f62-4465-994e-e95ac27d8ada
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: becd452525b999e0a23810aefd2455ee74ab0c67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="makevalid-geography-data-type"></a>MakeValid (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Преобразует **geography** экземпляр, который не является допустимым в допустимый **geography** экземпляра с допустимым типом Open Geospatial Consortium (OGC).  
  
 Если входной объект возвращает значение False для STIsValid(), `MakeValid()` преобразует экземпляр, который не является допустимым на допустимый экземпляр.  
  
 Это geography, тип данных поддерживает метод **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Этот метод может изменить тип **geography** экземпляра. Кроме того, точки **geography** экземпляр может переместиться немного. Некоторые методы, такие как NumPoint() результаты могут быть изменены.  
  
 В случаях, когда недопустимый пространственный экземпляр пересекает экватор и имеет EnvelopeAngle() = 180, **FullGlobe** экземпляра будут возвращены. `MakeValid()` **Geography** метода типа данных сделает лучший попытка вернуть допустимый экземпляр, но точность результатов не гарантируется.  
  
> [!NOTE]  
>  Недопустимые объекты могут быть сохранены в базе данных. Методы, которые могут быть выполнены к недопустимым экземплярам (для которых STIsValid() такие экземпляры возвращают False), методы, которые проверяют правильность или допускают экспорт: STIsValid(), MakeValid(), STAsText(), STAsBinary(), ToString() AsTextZM() и AsGml().  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В первом примере создается недопустимый экземпляр `LineString`, который перекрывает сам себя, и используется метод `STIsValid()`, чтобы подтвердить, что этот экземпляр является недопустимым. Функция `STIsValid()` возвращает значение 0 для недопустимого экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 4326);  
SELECT @g.STIsValid();  
```  
  
 Во втором примере, чтобы преобразовать экземпляр в допустимый и проверить, что этот экземпляр действительно допустим, используется метод `MakeValid()`. `STIsValid()`Возвращает значение 1 для допустимого экземпляра.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 В третьем примере проверяется, как был изменен экземпляр для преобразования его в допустимый.  
  
```  
SELECT @g.ToString();  
```  
  
 В этом примере при выборе экземпляра `LineString` значения возвращаются так же, как при использовании допустимого экземпляра `MultiLineString`.  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
## <a name="see-also"></a>См. также:  
 [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
