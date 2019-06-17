---
title: Типы данных интервала | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- second intervals [ODBC]
- data types [ODBC], interval data types
- interval data type [ODBC]
- day-time intervals [ODBC]
- intervals [ODBC], about intervals
- minute intervals [ODBC]
- day intervals [ODBC]
- year intervals [ODBC]
- month intervals [ODBC]
- interval data type [ODBC], about interval data types
- SQL data types [ODBC], interval
- year-month intervals [ODBC]
- C data types [ODBC], interval
- interval fields [ODBC]
ms.assetid: fba93f65-c1db-44f4-91ba-532f87241cf7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 930a848ea01d128cb248c7929408ce7510937ad9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188899"
---
# <a name="interval-data-types"></a>Интервальные типы данных
Интервал определяется как разница между двумя значениями даты и времени. Интервалы выражаются в одном из двух способов. Он *год месяц* интервала, который выражает интервалов с точки зрения лет и месяцев целого числа. Другой — *времени дня* интервал, который выражает интервалов с точки зрения дней, минуты и секунды. Эти два типа, интервалов отличаются, а не может одновременно, так как месяцев может иметь различное количество дней.  
  
 Интервал состоит из набора полей. Нет, подразумеваемый порядок среди полей. К примеру в интервале год месяц года первым, а затем по месяцам. Аналогичным образом в течение дня для минут, поля, имеющиеся в порядке день, час и минуту. Первое поле в тип интервала называется *начальные* поля, или *старшие* поля. Последнее поле называется *конечные* поля.  
  
 В всех интервалов ведущих поля не ограничивается правила григорианского календаря. Например в час минутный интервал времени, из поля часа не ограничен находиться в диапазоне от 0 до 23 (включительно), так как это обычно. Конечные поля после поле начальные выполните обычные ограничения григорианского календаря. Дополнительные сведения см. в разделе [ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)далее в этом приложении.  
  
 Существует 13 интервальных типов данных SQL и типы данных C 13 интервал. Каждый из типов данных интервала C использует ту же структуру, SQL_INTERVAL_STRUCT, для хранения данных, интервал. (Дополнительные сведения см. следующий раздел, [структура Interval C](../../../odbc/reference/appendixes/c-interval-structure.md).) Дополнительные сведения о типах данных SQL см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md); см. Дополнительные сведения о типах данных C, [типы данных C](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Идентификатор типа|Class|Описание|  
|---------------------|-----------|-----------------|  
|MONTH|Год месяц|Число месяцев между двумя датами.|  
|YEAR|Год месяц|Число лет между двумя датами.|  
|YEAR_TO_MONTH|Год месяц|Число лет и месяцев между двумя датами.|  
|DAY|Дневное время|Число дней между двумя датами.|  
|HOUR|Дневное время|Число часов между двумя даты/времени.|  
|MINUTE|Дневное время|Число минут между двумя даты/времени.|  
|SECOND|Дневное время|Количество секунд между двумя даты/времени.|  
|DAY_TO_HOUR|Дневное время|Количество дней/часов между двумя даты/времени.|  
|DAY_TO_MINUTE|Дневное время|Количество дней/часов или минут между двумя даты/времени.|  
|DAY_TO_SECOND|Дневное время|Количество дней/часов/минут/секунд между двумя даты/времени.|  
|HOUR_TO_MINUTE|Дневное время|Количество часов или минут между двумя даты/времени.|  
|HOUR_TO_SECOND|Дневное время|Количество часов/минут/секунд между двумя даты/времени.|  
|MINUTE_TO_SECOND|Дневное время|Количество минут или секунд между двумя даты/времени.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Структура Interval (C)](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Точность интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Длина интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Литералы интервала](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Переопределение заданной по умолчанию точности ведущего значения и точности значения долей секунды для интервальных типов данных](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
