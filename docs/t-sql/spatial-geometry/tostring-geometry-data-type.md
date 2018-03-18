---
title: "ToString (тип данных geometry) | Документы Майкрософт"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 614ecad2f669fed40ac5fd7ca30b994bedb0ac6e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="tostring-geometry-data-type"></a>ToString (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает представление WKT консорциума OGC геометрического объекта, дополненного всеми значениями Z (уровень) и M (мера) этого экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **nvarchar(max)**  
  
 Тип возвращаемых данных CLR: **SqlString**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает строку «Null», если он вызван для неопределенного экземпляра.  
  
 Вызов этого метода по отношению к определенным экземплярам эквивалентен использованию метода `AsTextZM().`  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере создается экземпляр `LineString` и используется метод `ToString()` для выборки текстового описания экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STAsText (тип данных geometry)](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

