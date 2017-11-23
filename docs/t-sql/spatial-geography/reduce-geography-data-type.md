---
title: "Уменьшить (тип данных geography) | Документы Microsoft"
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
- Reduce_TSQL
- Reduce
dev_langs: TSQL
helpviewer_keywords: Reduce method
ms.assetid: c5dfa8c1-6764-41d8-9150-f3cb30633d3e
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65b9276d3feea6e72f5404fa8f4d7eef963dbe78
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="reduce-geography-data-type-"></a>Reduce (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает приближение заданного **geography** экземпляра, полученное путем выполнения алгоритма Дугласа-Пекера для экземпляра с заданным допуском.  
  
 Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Аргументы  
  
|||  
|-|-|  
|Термин|Определение|  
|*отказоустойчивость*|Значение типа **float**. *Отклонение* представляет собой допуск, передаваемую в алгоритм Дугласа-Пекера. *Отклонение* должно быть положительным числом.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Для типов коллекции этот алгоритм работает независимо для каждого **geography** содержащиеся в экземпляре. Этот алгоритм не изменяет **точки** экземпляров.  
  
 Этот метод выполнит попытку сохранения конечных точек **LineString** экземпляров, но не сможет сделать это для сохранения действительного результата.  
  
 Если `Reduce()` вызывается с отрицательным значением, то будет вызвано **ArgumentException**. Отклонения, используемые в функции `Reduce()`, должны быть положительными.  
  
 Применяется алгоритм Дугласа-Пекера для каждой кривой или кольца в **geography** экземпляра путем удаления всех точек, за исключением начальной и конечной точки. Каждая удаленная точка затем добавляется обратно, начиная с самой удаленной точки, пока не останется точек более чем *отклонения* из результата. После этого результат преобразуется в допустимый при необходимости, поскольку гарантируется получение допустимого результата.  
  
 В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], этот метод расширен для **FullGlobe** экземпляров.  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и используется метод `Reduce()` для упрощения этого экземпляра.  
  
```  
DECLARE @g geography = 'LineString(120 45, 120.1 45.1, 199.9 45.2, 120 46)'  
SELECT @g.Reduce(10000).ToString()  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
