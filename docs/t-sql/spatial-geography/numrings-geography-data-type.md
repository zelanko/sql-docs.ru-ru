---
title: NumRings (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2d0b499db4ac3258d9ec3cdbeacc9e07c0ed39a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="numrings-geography-data-type"></a>NumRings (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает общее количество колец в экземпляре **Polygon**. В экземпляре типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** внешние и внутренние кольца неразличимы, поскольку любое кольцо может рассматриваться как внешнее.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип возвращаемых данных CLR: **SqlInt32**  
  
## <a name="remarks"></a>Примечания  
 Данный метод возвращает значение NULL, если переданный ему параметр — не экземпляр **Polygon**, и возвращает 0, если экземпляр пуст. Этот метод является точным.  
  
## <a name="examples"></a>Примеры  
 В этом примере создается экземпляр `Polygon` с двумя кольцами и выполняется проверка для подтверждения того, что он имеет два кольца.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
