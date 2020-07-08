---
title: NumRings (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 0f94b30d3f9f44fac2af7483ab0cfb7396666951
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85705885"
---
# <a name="numrings-geography-data-type"></a>NumRings (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает общее количество колец в экземпляре **Polygon**. В экземпляре типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** внешние и внутренние кольца неразличимы, поскольку любое кольцо может рассматриваться как внешнее.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип возвращаемых данных CLR: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Данный метод возвращает значение NULL, если переданный ему параметр — не экземпляр **Polygon**, и возвращает 0, если экземпляр пуст. Этот метод является точным.  
  
## <a name="examples"></a>Примеры  
 В этом примере создается экземпляр `Polygon` с двумя кольцами и выполняется проверка для подтверждения того, что он имеет два кольца.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
