---
description: HasМ (тип данных geometry)
title: HasM (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- HasM geometry
ms.assetid: 15540837-c4bf-4d18-b380-13ae31f3226f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fa0f82d9ee71c8fb5174a4ee4d48c706315f97e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458983"
---
# <a name="hasm-geometry-datatype"></a>HasМ (тип данных geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает значение 1 (true), если пространственный объект содержит по крайней мере одно значение M. В противном случае возвращает значение 0 (false).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.HasM  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **Boolean**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
  
```sql  
DECLARE @p GEOMETRY = 'Point(1 1 1 1)'  
SELECT @p.HasM   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M (тип данных geometry)](../../t-sql/spatial-geometry/m-geometry-data-type.md)  
  
