---
title: STPointN (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointN_TSQL
- STPointN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN (geometry Data Type)
ms.assetid: 8f0bb3b7-5cd9-42c2-b9f8-f04628653bd0
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 598f292c88cdd8516610df7b9a8b0a64424fab1d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762217"
---
# <a name="stpointn-geometry-data-type"></a>STPointN (тип данных geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает конкретную точку в экземпляре **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение типа **int** от 1 до количества точек в экземпляре **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
 Тип открытого геопространственного консорциума (OGC): **Point**  
  
## <a name="remarks"></a>Remarks  
 Если экземпляр **geometry** создан пользователем, то метод `STPointN()` возвращает точку, указанную в *expression* путем размещения точек в порядке, в котором они были первоначально введены.  
  
 Если экземпляр **geometry** был создан системой, то метод `STPointN()` возвращает точку, определяемую выражением *expression* путем размещения всех точек в том же порядке, в котором они будут выведены: сначала по геометрическим объектам, затем по кольцам внутри геометрического объекта (если применимо), а затем по точкам внутри кольца. Это порядок является детерминированным.  
  
 Если этот метод вызывается со значением менее 1, то будет вызвано исключение **ArgumentOutOfRangeException**.  
  
 Если этот метод вызывается со значением, превышающим число точек в экземпляре, он возвращает значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString`, и при помощи метода `STPointN()` производится получение второй точки в его описании.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

