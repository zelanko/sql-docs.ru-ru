---
title: IsNull (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f9b97eaa73b70beea9e56b2e4a07e99ea9e9e83
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="isnull-geometry-data-type"></a>IsNull (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Тип экземпляра **geometry** — NULL. Возвращает значение 0, если экземпляр отличен от NULL.
  
## <a name="syntax"></a>Синтаксис  
  
```  
.IsNull  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Метод `IsNull` позволяет проверить, имеет ли экземпляр **geometry** значение NULL. Это может привести к неочевидному результату, так как, если экземпляр имеет значение, отличное от NULL, возвращается значение 0, а если экземпляр имеет значение NULL, возвращается значение NULL.  
  
 Этот метод в основном используется инфраструктурой SQL Server; не рекомендуется использовать `IsNull` для проверки, имеет ли экземпляр значение NULL.  
  

## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

