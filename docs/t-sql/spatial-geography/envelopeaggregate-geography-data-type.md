---
title: EnvelopeAggregate (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8484b43ba5c2ed9e325f58430798ccf4921617b0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает ограничивающий объект для заданного набора объектов **geography**. Итоговый объект **geography** содержит несколько сегментов дуги.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_operand*  
 Столбец таблицы типа **geography**, в котором содержится набор объектов **geography**, используемых при выполнении операции Envelope Aggregate.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
## <a name="remarks"></a>Remarks  
 Если итоговый ограничивающий объект больше полушария, то возвращается объект **FullGlobe**. Этот метод не является точным.  
  
 Метод возвращает значение **NULL**, если во входных данных содержатся различные идентификаторы пространственных ссылок. См. раздел [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Метод не обрабатывает входные значения **NULL**.  
  
> [!NOTE]  
>  Метод возвращает значение **NULL**, если входными являются значения **NULL**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется операция `EnvelopeAggregate` в наборе различных географических точек **geography** в границах города.  
  
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
  
  
