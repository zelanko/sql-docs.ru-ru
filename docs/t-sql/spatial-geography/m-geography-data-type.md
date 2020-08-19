---
description: M (тип данных geography)
title: M (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- M (geography Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M method
ms.assetid: cdba04f0-4e17-48f6-bafb-b1f918c5a501
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 77a79972671854e7e8538de7b943545955f61e89
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422428"
---
# <a name="m-geography-data-type"></a>M (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает значение **M** (мера) для экземпляра **geography**. Семантика значения измерения определяется пользователем, но в основном описывает расстояние вдоль объекта типа linestring. Например, значение меры может использоваться для отсчета километровых столбов вдоль дороги.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.M  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Значение этого свойства равно NULL, если экземпляр **geography** не имеет тип **Point**, а также для любого экземпляра **Point**, для которого он не установлен.  
  
 Это свойство доступно только для чтения.  
  
 Значения M не используются в библиотечных вычислениях и поэтому не будут передаваться в библиотеку.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Point` со значениями Z (уровень) и M (мера) и используется метод `M`, чтобы получить значение `M` экземпляра.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z (тип данных geography)](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
