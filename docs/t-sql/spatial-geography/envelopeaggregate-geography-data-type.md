---
title: "EnvelopeAggregate (тип данных geography) | Документы Microsoft"
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
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs: TSQL
helpviewer_keywords: EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dc24295c305c4cc2ea2e4b6ff5fb3525a315f3d6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает ограничивающий объект для заданного набора **geography** объектов. Итоговый **geography** объект содержит несколько сегментов дуги.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_operand*  
 — **Geography** столбец таблицы типа, который содержит набор из **geography** объектов, для которого следует выполнить конверт статистические операции.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
## <a name="remarks"></a>Замечания  
 Объект **FullGlobe** возвращается, если итоговый ограничивающий объект больше полушария. Этот метод не является точным.  
  
 Метод возвращает **null** Если входные данные с различными идентификаторами SRID. В разделе [идентификаторы пространственных ссылок &#40; SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Метод игнорирует **null** входных данных.  
  
> [!NOTE]  
>  Метод возвращает **null** при входе присутствуют только значения **null**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется `EnvelopeAggregate` на наборе **geography** расположение точек в границах города.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::EnvelopeAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические географические методы](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
