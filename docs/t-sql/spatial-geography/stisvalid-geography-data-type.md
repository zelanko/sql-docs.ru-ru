---
title: "STIsValid (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid method (geography)
ms.assetid: 1bfe787f-ddf0-4fc7-af6a-570a58faab23
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2149008613cf38f1d4e3ac138afd776e16f4250b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stisvalid-geography-data-type"></a>STIsValid (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает значение true, если **geography** экземпляр является корректным и распознается как допустимый географический объект на основе типа Open Geospatial Consortium (OGC). Возвращает значение false, если **geography** экземпляр не является правильным. Этот метод является точным.  
  
 Это geography, тип данных поддерживает метод **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
 Тип OGC **geography** экземпляра можно определить путем вызова [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]формирует только допустимые **geography** экземпляров, но обеспечивает для хранения и получать недопустимые экземпляры. Допустимый экземпляр, представляющий тот же набор точек, что и недопустимый экземпляр, может быть получен с помощью метода `MakeValid()`.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `geography` и используется метод `STIsValid()`, чтобы проверить, допустим ли экземпляр.  
  
```  
DECLARE @g geography = geography::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 4326);  
SELECT @g.STIsValid();  
DECLARE @g geography  
```  
  
## <a name="see-also"></a>См. также:  
 [STGeometryType &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)   
 [MakeValid (тип данных geography)](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
