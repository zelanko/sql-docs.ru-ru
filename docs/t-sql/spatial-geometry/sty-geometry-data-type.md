---
title: "STY (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STY_TSQL
- STY (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STY (geometry Data Type)
ms.assetid: f72e0eaa-7d1d-4052-88fd-a172d8cb0d71
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1f1478a2a92d756653c6c2435590a7a2bfeeed1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sty-geometry-data-type"></a>STY (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Координата Y свойство **точки** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STY  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип: **число с плавающей запятой**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 Значение этого свойства будет иметь значение null при **geometry** экземпляр — это точка. Это свойство предназначено только для чтения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` и используется метод `STY`, чтобы получить координату экземпляра по оси Y.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STY;  
```  
  
## <a name="see-also"></a>См. также:  
 [STX (тип данных geometry)](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STSrid &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


