---
title: "Типы данных интервала | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a1b1a7320feef3cff6d63ce5ca6a22be6329169
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="interval-data-types"></a>Типы данных интервала
Интервал определяется как разница между двумя значениями даты и времени. Интервалы времени выражаются в одном из двух способов. Один является *год месяц* интервала, который выражает интервалы в лет и целое число месяцев. Другой подход — *дневное время* интервала, который выражает интервалы в днях, минуты и секунды. Эти два типа интервалов отличаются друг от друга и не может одновременно, так как месяцев может иметь различное количество дней.  
  
 Интервал состоит из набора полей. Нет, подразумеваемые упорядочение к полям. Например в течение интервала год месяц года идет первой, следуют за месяц. Аналогичным образом в течение дня минутного интервала поля находятся в порядке день, час и минуту. Первое поле в тип интервала называется *начальные* поля, или *старшие* поля. Последнее поле называется *конечные* поля.  
  
 В всех интервалов начальные поля не ограничивается правилами григорианского календаря. Например в час минута интервал времени, поле часов не ограничен находиться в диапазоне от 0 до 23 включительно, как обычно. Конечные поля после начальные поле выполните обычные ограничения григорианского календаря. Дополнительные сведения см. в разделе [ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)далее в этом приложении.  
  
 Существует 13 интервальных типов данных SQL и 13 интервальных типов данных C. Каждый из типов данных C интервал использует ту же структуру SQL_INTERVAL_STRUCT, для хранения данных интервала. (Дополнительные сведения см. следующий раздел, [C интервал структуры](../../../odbc/reference/appendixes/c-interval-structure.md).) Дополнительные сведения о типах данных SQL см. в разделе [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md); см. Дополнительные сведения о типах данных C, [типы данных C](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Идентификатор типа|Class|Description|  
|---------------------|-----------|-----------------|  
|MONTH|Месяц года|Число месяцев между двумя датами.|  
|YEAR|Месяц года|Число лет между двумя датами.|  
|YEAR_TO_MONTH|Месяц года|Число лет и месяцев между двумя датами.|  
|DAY|Время дня|Число дней между двумя датами.|  
|HOUR|Время дня|Количество часов между двумя даты/времени.|  
|MINUTE|Время дня|Количество минут между двумя даты/времени.|  
|SECOND|Время дня|Количество секунд между двумя даты/времени.|  
|DAY_TO_HOUR|Время дня|Количество дней или часов между двумя даты/времени.|  
|DAY_TO_MINUTE|Время дня|Число дней или часов или минут между двумя даты/времени.|  
|DAY_TO_SECOND|Время дня|Число дней или часов или минут и секунд между двумя даты/времени.|  
|HOUR_TO_MINUTE|Время дня|Количество часов или минут между двумя даты/времени.|  
|HOUR_TO_SECOND|Время дня|Количество часов или минут или секунд между двумя даты/времени.|  
|MINUTE_TO_SECOND|Время дня|Число минут и секунд между двумя даты/времени.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Структура Interval (C)](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Точность интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Длина интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Литералы интервала](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Переопределение заданной по умолчанию точности ведущего значения и точности значения долей секунды для интервальных типов данных](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
