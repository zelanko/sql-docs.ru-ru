---
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
ms.openlocfilehash: fe68a2179659a3e5d9cd941d613deb954dbf4726
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731216"
---
# <a name="astextzm-geography-data-type"></a>AsTextZM (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает представление WKT открытого геопространственного консорциума (OGC) для экземпляра **geography**, дополненное всеми значениями **Z** (высота) и **M** (мера) этого экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsTextZM ()  
```  
  
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
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M (тип данных geography)](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Z (тип данных geography)](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
