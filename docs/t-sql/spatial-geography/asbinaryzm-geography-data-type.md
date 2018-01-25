---
title: "AsBinaryZM (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsBinaryZM
- AsBinaryZM_TSQL
dev_langs: TSQL
helpviewer_keywords:
- AsBinaryZM, geography
- AsBinaryZM
ms.assetid: 37246adb-814d-4113-9983-4d336de8182c
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99981d95095b97dd599787578f891a39e60098ac
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="asbinaryzm-geography-data-type"></a>AsBinaryZM (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает представление Open Geospatial Consortium (OGC) Well-Known Binary (WKB) **geometry** экземпляр дополненного **Z** (высота) и **M** (Мера) значения, сопровождающих экземпляр.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsBinaryZM()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **varbinary(max)**  
  
 Возвращаемый тип CLR: **SqlBytes**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
  
```sql  
DECLARE @g1 GEOGRAPHY = 'Point(1 1 2 3)';  
  
SELECT @g1.STAsBinary();  
-- Returns: 0x0101000000000000000000F03F000000000000F03F  
  
SELECT @g1.AsBinaryZM();  
--Returns: 0x01B90B0000000000000000F03F000000000000F03F00000000000000400000000000000840  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [М &#40; тип данных geography &#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Я &#40; тип данных geography &#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
