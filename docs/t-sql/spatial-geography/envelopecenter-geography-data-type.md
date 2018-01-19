---
title: "EnvelopeCenter (тип данных geography) | Документы Microsoft"
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
f1_keywords:
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs: TSQL
helpviewer_keywords: EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07b46f0d198fe2e90456252c9b1ad95669cfc478
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="envelopecenter-geography-data-type-"></a>EnvelopeCenter (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает точку, которую можно использовать как центр ограничивающей окружности для **geography** экземпляра.  
  
 Чтобы определить ограничивающую окружность, все точки в экземпляре описываются как вектор от центра Земли к точке на поверхности Земли. Центральная точка ограничивающей окружности рассчитывается как среднее значение всех векторов. Для закрытых циклов, либо в **многоугольника** экземпляра или **linestring** экземпляра, первая и последняя точка используются только один раз.  
  
 Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EnvelopeCenter( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает **точки**. При использовании с `EnvelopeAngle()`, `EnvelopeCenter()` возвращает ограничивающую окружность **geography** экземпляра.  
  
> [!NOTE]  
>  `EnvelopeCenter()`Возвращает ограничивающую окружность для **geography** экземпляр, но результаты не гарантируется для получения минимальной ограничивающей окружности. Напротив **geometry** метода типа данных `STEnvelope()` гарантирует возврат минимального ограничивающего прямоугольника при применении к **geometry** экземпляра.  
  
 В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях возвращает центр окружности, представляющей огибающую этого экземпляра в виде **точки**. Для всех больших объектов, определенных параметром `EnvelopeAngle()` = 180 `EnvelopeCenter()` возвращает значение (90,0).  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeAngle &#40; тип данных geography &#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  
