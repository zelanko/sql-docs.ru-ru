---
title: "ToString (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ToString (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 34e028dcd1a9fd141d0771e1b410d469d6dbd47c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="tostring-geography-data-type"></a>ToString (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает представление Open Geospatial Consortium (OGC) Well-Known Text (WKT) **geography** экземпляра, дополненное всеми значениями Z (уровень) и значения M (Мера), сопровождающими экземпляр.  
  
 Это geography, тип данных поддерживает метод **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **nvarchar(max)**  
  
 Возвращаемый тип CLR: **SqlString**  
  
## <a name="remarks"></a>Замечания  
 Метод возвращает строку NULL при вызове на экземплярах NULL. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], набор возможных результатов на сервере была расширена для **FullGlobe** экземпляров. Этот метод возвратит такое же значение, что и функция `AsTextZM()`.  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `LineString` и с помощью `ToString()` возвращается текстовое описание экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM (тип данных geography)](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  

