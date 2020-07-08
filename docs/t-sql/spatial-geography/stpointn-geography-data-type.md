---
title: STPointN (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointN_TSQL
- STPointN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN method
ms.assetid: 47670feb-b9e0-4b4b-af83-b9bba7da66ac
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 75db9df496282ba6b1ef78012164e13682d5b11e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85702294"
---
# <a name="stpointn-geography-data-type"></a>STPointN (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает указанную точку в экземпляре **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение типа **int** со значением в диапазоне от 1 до числа точек в экземпляре **geography**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
 Тип открытого геопространственного консорциума (OGC): **Point**  
  
## <a name="remarks"></a>Remarks  
 Если экземпляр **geography** создан пользователем, то метод STPointN() возвращает точку, указанную *expression* путем размещения точек в порядке, в котором они были первоначально введены.  
  
 Если экземпляр **geography** формируется системой, метод STPointN() возвращает точку, указанную *expression* путем упорядочения всех точек в той последовательности, в которой они должны быть выведены: сначала по экземпляру **geography**, затем по кольцу в пределах экземпляра (если это применимо), после чего по точкам кольца. Это порядок является детерминированным.  
  
 Если этот метод вызывается со значением менее 1, то будет вызвано исключение **ArgumentOutOfRangeException**.  
  
 Если этот метод вызывается со значением, превышающим число точек в экземпляре, он возвращает значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString`, и при помощи метода `STPointN()` производится получение второй точки в его описании.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
