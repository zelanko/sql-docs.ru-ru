---
title: UnionAggregate (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- UnionAggregate method (geometry)
ms.assetid: dc7929cc-55ca-4a2c-a4b9-f5452f95bde8
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 696d8d8c98ffb808e5e6d1afbeaf27733bc1ecef
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36251506"
---
# <a name="unionaggregate-geometry-data-type"></a>UnionAggregate (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Выполняет операцию объединения на наборе объектов типа geometry.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UnionAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_operand*  
 Столбец таблицы типа **geometry**, в котором содержится набор объектов **geometry**, с которыми выполняется операция объединения.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
## <a name="exceptions"></a>Исключения  
 Вызывает исключение `FormatException` при наличии недопустимых входных значений. См. раздел [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md).  
  
## <a name="remarks"></a>Remarks  
 Метод возвращает значение **NULL**, если входные данные пусты или содержат различные идентификаторы пространственных ссылок. См. раздел [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Метод не обрабатывает входные значения **NULL**.  
  
> [!NOTE]  
>  Метод возвращает значение **NULL**, если входными являются значения **NULL**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает объединение для набора объектов **geometry** в табличных переменных.  
 ```
 -- Setup table variable for UnionAggregate example 
 DECLARE @Geom TABLE 
 ( 
 shape geometry, 
 shapeType nvarchar(50) 
 ); 
 INSERT INTO @Geom(shape,shapeType) 
 VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'), 
 ('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle'); 
 -- Perform UnionAggregate on @Geom.shape column 
 SELECT geometry::UnionAggregate(shape).ToString() 
 FROM @Geom;
``` 
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

