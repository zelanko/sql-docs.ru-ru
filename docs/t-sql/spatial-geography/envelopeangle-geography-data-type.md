---
title: "EnvelopeAngle (тип данных geography) | Документы Microsoft"
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
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cd410a6eb07c626c7674febad2a427bbd029f98a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает максимальный угол между точкой, возвращаемой методом `EnvelopeCenter()` и точкой в **geography** экземпляра в градусах.  
  
 Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **число с плавающей запятой**  
  
 Возвращаемый тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 Этот метод возвращает точку в **geography** экземпляра в градусах. При использовании с EnvelopeCenter(), `EnvelopeAngle()` возвращает ограничивающую окружность **geography** экземпляра.  
  
 В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], этот метод расширен для **FullGlobe** экземпляров.  
  
 Ограничение полушария, применяемое к `EnvelopeAngle()` в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] был удален. Однако будут возвращены экземпляры с углами более 90 градусов, 180 градусов. `EnvelopeAngle()`не является точным для **geography** экземпляров, охватывающих более одного полушария.  
  
## <a name="examples"></a>Примеры  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40; тип данных geography &#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  

