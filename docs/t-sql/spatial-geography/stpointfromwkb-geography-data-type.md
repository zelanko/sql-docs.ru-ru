---
description: STPointFromWKB (географический тип данных)
title: STPointFromWKB (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointFromWKB_TSQL
- STPointFromWKB (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB method
ms.assetid: b3b4e3bb-47bc-4621-99c4-c97aa60cdf8b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 70eabd3b36ad564b02d16e3ce906405d83a55730
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88459030"
---
# <a name="stpointfromwkb-geography-data-type"></a>STPointFromWKB (географический тип данных)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает экземпляр **geographyPoint** из WKB-представления OGC.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STPointFromWKB ( 'WKB_point' , SRID )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *WKB_point*  
 Представление в формате WKB возвращаемого экземпляра **geographyPoint**. *WKB_point* — это выражение типа **varbinary(max)**.  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geographyPoint**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
 Тип OGC: **Point**  
  
## <a name="remarks"></a>Комментарии  
 Если входные данные имеют неверный формат, метод вызовет исключение **FormatException**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STPointFromWKB()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STPointFromWKB(0x010100000017D9CEF753D347407593180456965EC0, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические географические методы OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
