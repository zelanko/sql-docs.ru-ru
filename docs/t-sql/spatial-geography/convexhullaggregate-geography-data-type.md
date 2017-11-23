---
title: "ConvexHullAggregate (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 07/30/2017
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
- ConvexHullAggregate_TSQL
- ConvexHullAggregate
dev_langs: TSQL
helpviewer_keywords: ConvexHullAggregate method (geography)
ms.assetid: 21784c66-2725-471b-9e2d-a8c2e3695197
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 726bcc637e827c37000112cf66b81dad4e0f691b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="convexhullaggregate-geography-data-type"></a>ConvexHullAggregate (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает выпуклую оболочку для заданного набора **geography** объектов.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_operand*  
 — **Geography** столбец таблицы типа, представляющий набор **geography** объектов.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
## <a name="exception"></a>Exception  
 Вызывает исключение `FormatException` при наличии недопустимых входных значений. В разделе [STIsValid &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Замечания  
 Метод возвращает **null** при входных данных пуст или содержит различными идентификаторами SRID. В разделе [идентификаторы пространственных ссылок &#40; SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Метод игнорирует **null** входных данных.  
  
> [!NOTE]  
>  Метод возвращает **null** при входе присутствуют только значения **null**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается выпуклая оболочка набора **geography** объектов.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::ConvexHullAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические географические методы](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
