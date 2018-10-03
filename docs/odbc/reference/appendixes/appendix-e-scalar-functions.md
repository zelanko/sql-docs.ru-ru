---
title: Приложение д. скалярные функции | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 94e33460d3c50363e96e90fb457467b8e5cda315
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631862"
---
# <a name="appendix-e-scalar-functions"></a>Приложение Д. Скалярные функции
ODBC определяет следующие скалярные функции, с подробными сведениями о каждом из этих типов функции, в соответствующих разделах данного приложения. Описания функции содержат синтаксис.  
  
 Это приложение содержит следующие разделы.  
  
-   [Строковые функции](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Числовые функции](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Функции даты, времени и интервалов](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Системные функции](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Функция явного преобразования типа данных](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [Функция CAST SQL-92](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 Так как функции часто являются связанными с источником данных ODBC не требует тип данных для возвращаемых значений из скалярных функций. Приложения должны использовать скалярная функция CONVERT всякий раз, когда возможность принудительно выполнить преобразование типов данных.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Скалярные функции ODBC и SQL-92  
 Таблицы в этом приложении включают функции, которые были добавлены в ODBC 3.0 в соответствии со стандартом SQL-92. Эти функции добавлены для определенного типа скалярные функции, как определено в ODBC, отображаются в каждом разделе.  
  
 Классифицировать их скалярные функции ODBC и SQL-92 по-разному. ODBC классифицирует скалярные функции, тип аргумента; SQL-92 классифицирует их по возвращаемое значение. Например функция EXTRACT классифицируется как функций timedate в ODBC, так как аргумент извлечение поля является ключевым словом datetime и источника извлечения аргументом является выражение даты-времени или интервал. SQL-92, с другой стороны, классифицирует ИЗВЛЕЧЕНИЯ как числовые скалярной функцией, так как возвращаемое значение является числовым.  
  
 Приложение может определить какие скалярных функций, которые поддерживает драйвер путем вызова **SQLGetInfo**. Типы сведений включаются, ODBC и SQL-92 классификации скалярных функций. Так как эти классификации отличаются, поддержки для некоторых скалярных функций может указывается в типы сведений, которые не соответствуют ODBC и SQL-92. Например поддержка для ИЗВЛЕЧЕНИЯ в ODBC обозначается тип сведений SQL_TIMEDATE_FUNCTIONS; Поддержка ИЗВЛЕЧЕНИЯ в SQL-92, с другой стороны, обозначается тип SQL_SQL92_NUMERIC_VALUE_FUNCTIONS сведений.
