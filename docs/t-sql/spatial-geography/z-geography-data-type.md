---
title: "Z (тип данных geography) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
f1_keywords:
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f1f0677d96fe12f8b425b54a63ac57bedb4a155
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="z-geography-data-type"></a>Z (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Значение Z (высота) экземпляра. Семантика значения высоты определяется пользователем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Значение этого свойства равно NULL, если экземпляр **geography** не имеет тип Point, а также для любого экземпляра **Point**, для которого оно не задано.  
  
 Это свойство доступно только для чтения.  
  
 Координаты по оси Z не используются ни в каких вычислениях, выполненных библиотекой, и не проходят ни через какие библиотечные изменения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` со значениями Z (высота) и M (мера) и методом `Z` производится получение для него значения Z.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M (тип данных geography)](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM (тип данных geography)](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
