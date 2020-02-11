---
title: Приложение E. скалярные функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bb5f16485312979e9fb2ad6b3a95dacb79b695d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996181"
---
# <a name="appendix-e-scalar-functions"></a>Приложение Д. Скалярные функции
ODBC определяет следующие типы скалярных функций с подробными сведениями о каждом из этих типов функций, представленных в соответствующих разделах этого приложения. Описания функций включают в себя соответствующий синтаксис.  
  
 Это приложение содержит следующие разделы.  
  
-   [Строковые функции](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Числовые функции](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Функции даты, времени и интервалов](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Системные функции](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Функция явного преобразования типа данных](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [Функция CAST SQL-92](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC не требует типа данных для возвращаемых значений скалярных функций, поскольку эти функции часто зависят от источника данных. Приложения должны использовать скалярную функцию CONVERT везде, где это возможно, для принудительного преобразования типов данных.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Скалярные функции ODBC и SQL-92  
 Таблицы в этом приложении включают функции, добавленные в ODBC 3,0 для согласования с SQL-92. Эти функции, добавленные для определенного типа скалярной функции, как определено в ODBC, указаны в каждом разделе.  
  
 ODBC и SQL-92 классифицируют свои скалярные функции по-разному. ODBC классифицирует скалярные функции по типу аргумента; SQL-92 классифицирует их по возвращаемому значению. Например, функция извлечения классифицируется как функция timedate в ODBC, поскольку аргумент Extract-Field является ключевым словом DateTime, а аргумент Extract-Source — выражением DateTime или Interval. SQL-92, с другой стороны, классифицирует извлечение в виде числовой скалярной функции, так как возвращаемое значение является числовым.  
  
 Приложение может определить, какие скалярные функции поддерживает драйвер, вызвав **SQLGetInfo**. Типы сведений включены как для ODBC, так и для классификаций SQL-92 скалярных функций. Так как эти классификации различаются, поддержка некоторых скалярных функций может быть указана в информационных типах, которые не соответствуют ODBC и SQL-92. Например, поддержка извлечения в ODBC обозначается типом сведений SQL_TIMEDATE_FUNCTIONS. поддержка извлечения в SQL-92, с другой стороны, определяется типом сведений SQL_SQL92_NUMERIC_VALUE_FUNCTIONS.
