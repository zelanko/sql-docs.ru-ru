---
title: MakeValid (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid method (geography)
ms.assetid: f67038e3-4f62-4465-994e-e95ac27d8ada
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d913a0e7bbe29ab6f6f303519c73304238afd7df
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68127396"
---
# <a name="makevalid-geography-data-type"></a>MakeValid (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Преобразует недопустимый экземпляр **geography** в допустимый экземпляр **geography** с допустимым типом OGC (Open Geospatial Consortium).  
  
 Если входной объект возвращает для STIsValid() значение False, то `MakeValid()` преобразует недопустимый экземпляр в допустимый.  
  
 Этот метод типа данных geography поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Применение этого метода может изменить тип экземпляра **geography**. Кроме того, оно может привести к небольшому сдвигу точек в экземпляре **geography**. Результаты выполнения некоторых методов, например NumPoint(), могут изменяться.  
  
 В тех случаях, когда недопустимый пространственный экземпляр пересекает экватор, а EnvelopeAngle() = 180, возвращается экземпляр **FullGlobe**. Метод типа данных `MakeValid()`**geography** сделает максимум, чтобы вернуть допустимый экземпляр, но точность результатов не гарантируется.  
  
> [!NOTE]  
>  Недопустимые объекты могут быть сохранены в базе данных. Методы, применимые к недопустимым экземплярам (то есть тем, для которых STIsValid() возвращает значение False), проверяют правильность или допускают экспорт: STIsValid(), MakeValid(), STAsText(), STAsBinary(), ToString(), AsTextZM() и AsGml().  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В первом примере создается недопустимый экземпляр `LineString`, который перекрывает сам себя, и используется метод `STIsValid()`, чтобы подтвердить, что этот экземпляр является недопустимым. Функция `STIsValid()` возвращает значение 0 для недопустимого экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 4326);  
SELECT @g.STIsValid();  
```  
  
 Во втором примере, чтобы преобразовать экземпляр в допустимый и проверить, что этот экземпляр действительно допустим, используется метод `MakeValid()`. Функция `STIsValid()` возвращает значение 1 для недопустимого экземпляра.  
  
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
  
  
