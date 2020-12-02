---
description: AsTextZM (тип данных geography)
title: AsTextZM (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsTextZM (geography Data Type)
- AsTextZM_TSQL
- AsTextZM
- AsTextZM_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM method
ms.assetid: e9dc27f6-e945-4457-8498-7644db34008e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 49857a94c95240386893854408d2b26cba533815
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96115163"
---
# <a name="astextzm-geography-data-type"></a>AsTextZM (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает представление WKT открытого геопространственного консорциума (OGC) для экземпляра **geography**, дополненное всеми значениями **Z** (высота) и **M** (мера) этого экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsTextZM ()  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **nvarchar(max)**  
  
 Тип возвращаемых данных CLR: **SqlChars**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере создается экземпляр `Point`, содержащий значения **Z** (высота) и **M** (мера). Метод `STAsText()` выбирает значения WKT (–122.34900 47.65100); метод `AsTextZM()` выбирает те же самые значения WKT, а также возвращает значения для **Z** и **M** (–122.34900 47.65100 10.3 12).  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M (тип данных geography)](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Z (тип данных geography)](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
