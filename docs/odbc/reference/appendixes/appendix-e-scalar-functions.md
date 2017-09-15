---
title: "Приложение д. скалярные функции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aaa110a6a62ca91535e790a267ef714675719bf4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-e-scalar-functions"></a>Приложение д скалярные функции
ODBC определяет следующие типы скалярных функций с подробными сведениями о каждом из этих типов функции, в соответствующих разделах данного приложения. Описания функции содержат синтаксис.  
  
 Это приложение содержит следующие разделы.  
  
-   [Строковые функции](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Числовые функции](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Интервал функции, даты и времени](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Системные функции](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Явный тип функции преобразования](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [Функции CAST SQL-92](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 Поскольку функции часто являются данными, определяемые источником ODBC не требует тип данных для возвращаемых значений из скалярных функций. Приложения должны использовать скалярная функция CONVERT всякий раз, когда возможно принудительное преобразование типов данных.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Скалярные функции ODBC и SQL-92  
 Таблицы в этом приложении включают функции, которые были добавлены в ODBC 3.0 в соответствии со стандартом SQL-92. Эти функции, добавленные для определенного типа скалярной функцией, как определено в ODBC, отображаются в каждом разделе.  
  
 Классифицировать их скалярных функций ODBC и SQL-92 по-разному. ODBC классифицирует скалярные функции, тип аргумента; SQL-92 классифицирует их по возвращаемое значение. Например функция EXTRACT классифицируется как функция timedate в ODBC, так как аргумент извлечения полей — это ключевое слово datetime и источника извлечения аргумент представляет собой выражение даты-времени или интервала. SQL-92, с другой стороны, классифицирует ИЗВЛЕЧЕНИЯ как числовые скалярной функцией, так как возвращаемое значение является числовым.  
  
 Приложение может определить, какие скалярных функций, драйвер поддерживает путем вызова **SQLGetInfo**. Типы данных включены для ODBC и SQL-92 классификации скалярных функций. Поскольку эти классификации отличаются, поддержка некоторых скалярных функций может указывается в типы данных, которые не соответствуют ODBC и SQL-92. Например поддержка для ИЗВЛЕЧЕНИЯ в ODBC обозначается тип SQL_TIMEDATE_FUNCTIONS сведения; с другой стороны, поддержка для ИЗВЛЕЧЕНИЯ в SQL-92, указанная типом SQL_SQL92_NUMERIC_VALUE_FUNCTIONS сведения.
