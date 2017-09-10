---
title: "M (тип данных geometry) | Документы Microsoft"
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
- M (geometry Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M (geometry Data Type)
ms.assetid: 443ae2ea-739b-41ef-96cc-ac5dfd65e10b
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0946bc24abaee28973f8afd409ac68d04a428c8d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="m-geometry-data-type"></a>M (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **M** (Мера) значение **geometry** экземпляра. Семантика значения этой меры определяется пользователем.  

## <a name="syntax"></a>Синтаксис  
  
```  
  
.M  
```  
  
## <a name="arguments"></a>Аргументы  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип: **число с плавающей запятой**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 Значение этого свойства равно null при **geometry** экземпляр не **точки**, а также для любого **точки** экземпляра, для которой не установлено.  
  
 Это свойство предназначено только для чтения.  
  
 **M** значения не используются ни в каких вычислениях, выполненных библиотекой и не будет выполнена через какие библиотечные изменения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` со значениями Z (уровень) и M (мера), а также используется выражение `M` для выборки значения M экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Я &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)   
 [AsTextZM (тип данных geometry)](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)  
  
  


