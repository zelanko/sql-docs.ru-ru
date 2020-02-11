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
ms.openlocfilehash: a42c8767228c75d3b7b0da308d739516875cf966
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947559"
---
# <a name="interval-data-types"></a>Интервальные типы данных
Интервал определяется как разница между двумя датами и временем. Интервалы выражаются одним из двух различных способов. Один из них — *год месяца* , который выражает интервалы в годах и целым числом месяцев. Второй — интервал *времени* , который выражает интервалы в днях, минутах и секундах. Эти два типа интервалов являются разными и не могут быть смешанными, так как месяцы могут иметь разное количество дней.  
  
 Интервал состоит из набора полей. Между полями имеется подразумеваемое упорядочение. Например, в течение интервала между пропуском года сначала указывается год, за которым следует месяц. Аналогичным образом, в течение ежедневного интервала поля находятся в том порядке, в котором указаны день, час и минута. Первое поле в типе интервала называется *начальным* полем или полем *высокого порядка* . Последнее поле называется *конечным* полем.  
  
 Во всех интервалах начальное поле не ограничивается правилами григорианского календаря. Например, в интервале от часа до минуты поле Hour не ограничивается от 0 до 23 (включительно), как обычно. Конечные поля, следующие за ведущим полем, следуют обычным ограничениям григорианского календаря. Дополнительные сведения см. в подразделе [ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)далее в этом приложении.  
  
 Существует 13 типов данных SQL и 13 интервалов данных с. Каждый из типов данных Interval C использует ту же структуру, SQL_INTERVAL_STRUCT, для хранения данных интервала. (Дополнительные сведения см. в следующем разделе [Структура интервала C](../../../odbc/reference/appendixes/c-interval-structure.md).) Дополнительные сведения о типах данных SQL см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md). Дополнительные сведения о типах данных C см. в разделе [типы данных c](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Идентификатор типа|Class|Description|  
|---------------------|-----------|-----------------|  
|MONTH|Год-месяц|Число месяцев между двумя датами.|  
|YEAR|Год-месяц|Число лет между двумя датами.|  
|YEAR_TO_MONTH|Год-месяц|Число лет и месяцев между двумя датами.|  
|DAY|Время дня|Число дней между двумя датами.|  
|HOUR|Время дня|Количество часов между двумя датами и временем.|  
|MINUTE|Время дня|Количество минут между двумя датами и временем.|  
|SECOND|Время дня|Число секунд между двумя датами и временем.|  
|DAY_TO_HOUR|Время дня|Число дней/часов между двумя датами и временем.|  
|DAY_TO_MINUTE|Время дня|Число дней/часов/минут между двумя датами и временем.|  
|DAY_TO_SECOND|Время дня|Число дней/часов/минут/секунд между двумя значениями даты и времени.|  
|HOUR_TO_MINUTE|Время дня|Число часов/минут между двумя датами и временем.|  
|HOUR_TO_SECOND|Время дня|Число часов/минут/секунд между двумя датами и временем.|  
|MINUTE_TO_SECOND|Время дня|Число минут/секунд между двумя датами и временем.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Структура Interval (C)](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Точность интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Длина интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Литералы интервала](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Переопределение заданной по умолчанию точности ведущего значения и точности значения долей секунды для интервальных типов данных](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
