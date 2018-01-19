---
title: "HasZ (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 05/05/2017
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
helpviewer_keywords: HasZ geometry
ms.assetid: aa378943-252a-4079-848b-6c59344fcfce
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 71a46abe72ce0b9d354d59cfbf0f1f678514e7ad
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="hasz-geometry-datatype"></a>HasZ (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает 1 (true), если пространственный объект содержит по крайней мере одно значение Z. В противном случае возвращает 0 (false).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.HasZ  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **Boolean**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
  
```sql  
DECLARE @p GEOMETRY = 'Point(1 1 1 1)'  
SELECT @p.HasZ   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Я &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  
