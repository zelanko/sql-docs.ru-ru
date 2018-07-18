---
title: Приложение д. скалярные функции | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: acaab68fab32c25ab101f65ccd196abe7ebceef2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914489"
---
# <a name="appendix-e-scalar-functions"></a>Приложение д скалярные функции
ODBC определяет следующие типы скалярных функций с подробными сведениями о каждом из этих типов функции, в соответствующих разделах данного приложения. Описания функции содержат синтаксис.  
  
 Это приложение содержит следующие разделы.  
  
-   [Строковые функции](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Числовые функции](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Функции даты, времени и интервалов](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Системные функции](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Функция явного преобразования типа данных](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [Функция CAST SQL-92](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 Поскольку функции часто являются данными, определяемые источником ODBC не требует тип данных для возвращаемых значений из скалярных функций. Приложения должны использовать скалярная функция CONVERT всякий раз, когда возможно принудительное преобразование типов данных.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Скалярные функции ODBC и SQL-92  
 Таблицы в этом приложении включают функции, которые были добавлены в ODBC 3.0 в соответствии со стандартом SQL-92. Эти функции, добавленные для определенного типа скалярной функцией, как определено в ODBC, отображаются в каждом разделе.  
  
 Классифицировать их скалярных функций ODBC и SQL-92 по-разному. ODBC классифицирует скалярные функции, тип аргумента; SQL-92 классифицирует их по возвращаемое значение. Например функция EXTRACT классифицируется как функция timedate в ODBC, так как аргумент извлечения полей — это ключевое слово datetime и источника извлечения аргумент представляет собой выражение даты-времени или интервала. SQL-92, с другой стороны, классифицирует ИЗВЛЕЧЕНИЯ как числовые скалярной функцией, так как возвращаемое значение является числовым.  
  
 Приложение может определить, какие скалярных функций, драйвер поддерживает путем вызова **SQLGetInfo**. Типы данных включены для ODBC и SQL-92 классификации скалярных функций. Поскольку эти классификации отличаются, поддержка некоторых скалярных функций может указывается в типы данных, которые не соответствуют ODBC и SQL-92. Например поддержка для ИЗВЛЕЧЕНИЯ в ODBC обозначается тип SQL_TIMEDATE_FUNCTIONS сведения; с другой стороны, поддержка для ИЗВЛЕЧЕНИЯ в SQL-92, указанная типом SQL_SQL92_NUMERIC_VALUE_FUNCTIONS сведения.
