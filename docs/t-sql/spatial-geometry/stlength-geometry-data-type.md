---
title: "STLength (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 476d1c761939c25ace4dbb67720537dd10a16531
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stlength-geometry-data-type"></a>STLength (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает общую длину элементов в **geometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **число с плавающей запятой**  
  
 Возвращаемый тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 Если **geometry** экземпляр закрыт, его длина вычисляется как общая длина вокруг экземпляра; длина любого многоугольника есть его периметр и длина точки — 0. Длина любого **geometrycollection** тип представляет собой сумму размеров всех содержащихся **geometry** экземпляров.  
  
 STLength() работает и с допустимыми и с недопустимыми объектами LineString. Обычно LineString является недопустимым вследствие перекрывающихся сегментов, которые могут быть вызваны аномалиями, например неточными трассировками GPS. STLength() не удаляет перекрывающиеся или недопустимые сегменты. Он включает перекрывающиеся и недопустимые сегменты в возвращаемое значение длины. Метод MakeValid() может удалять перекрывающиеся сегменты из LineString.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и метод `STLength()` получает его длину.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

