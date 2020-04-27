---
title: Преобразование данных из SQL в типы данных C | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC]
- data conversions from SQL to C types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- data types [ODBC], SQL data types
- SQL data types [ODBC], converting to C types
- converting data from SQL to c types [ODBC]
- converting data from SQL to c types [ODBC], about converting
- C data types [ODBC], converting from SQL types
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a10730cb3910c55679c264583801cd57c83bfc3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284754"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Преобразование данных из SQL в типы данных C
Когда приложение вызывает **SQLFetch**, **SQLFetchScroll**или **SQLGetData**, драйвер получает данные из источника данных. При необходимости он преобразует данные из типа данных, в котором драйвер извлекает их в тип данных, указанный в аргументе *TargetType* в **SQLBindCol** или **SQLGetData.** Наконец, он сохраняет данные в расположении, на которое указывает аргумент *таржетвалуептр* в **SQLBindCol** или **SQLGETDATA** (и поле SQL_DESC_DATA_PTR АРД).  
  
 В следующей таблице приведены поддерживаемые преобразования типов данных ODBC SQL в типы данных ODBC C. Заполненный круг обозначает преобразование по умолчанию для типа данных SQL (тип данных C, в который будут преобразованы данные, если значение *TargetType* — SQL_C_DEFAULT). Пустой кружок обозначает поддерживаемое преобразование.  
  
 Для приложения ODBC *3. x* , работающего с драйвером ODBC *2. x* , преобразование из типов данных, относящихся к драйверу, может не поддерживаться.  
  
 Формат преобразованных данных не зависит от параметра Country® Windows.  
  
 В таблицах в следующих разделах описывается, как драйвер или источник данных преобразуют данные, полученные из источника данных. драйверы необходимы для поддержки преобразований во все типы данных ODBC C из поддерживаемых ими типов данных ODBC SQL. Для данного типа данных ODBC SQL в первом столбце таблицы перечислены допустимые входные значения аргумента *TargetType* в **SQLBindCol** и **SQLGetData**. Во втором столбце перечислены результаты теста, часто используется аргумент *BufferLength* , указанный в **SQLBindCol** или **SQLGetData**, который драйвер выполняет для определения возможности преобразования данных. Для каждого результата в третьем и четвертом столбцах перечисляются значения, помещаемые в буферы, указанные в аргументах *таржетвалуептр* и *StrLen_or_IndPtr* , указанных в **SQLBindCol** или **SQLGetData** , после того, как драйвер предпринял попытку преобразования данных. (Аргумент *StrLen_or_IndPtr* соответствует полю SQL_DESC_OCTET_LENGTH_PTR объекта АРД.) В последнем столбце содержится значение SQLSTATE, возвращенное для каждого результата с помощью **SQLFetch**, **SQLFetchScroll**или **SQLGetData**.  
  
 Если аргумент *TargetType* в **SQLBindCol** или **SQLGetData** содержит идентификатор для типа данных ODBC C, который не показан в таблице для данного типа данных ODBC SQL, **SQLFETCH**, **SQLFetchScroll**или **SQLGetData** возвращает значение SQLSTATE 07006 (нарушение атрибута ограниченного типа данных). Если аргумент *TargetType* содержит идентификатор, указывающий преобразование из типа данных SQL, зависящего от драйвера, в тип данных ODBC C, а это преобразование не поддерживается драйвером, **SQLFetch**, **SQLFETCHSCROLL**или **SQLGetData** возвращает значение SQLSTATE HYC00 (дополнительная функция не реализована).  
  
 Хотя он не показан в таблицах, драйвер возвращает SQL_NULL_DATA в буфере, указанном аргументом *StrLen_or_IndPtr* , если значение данных SQL равно null. Описание использования *StrLen_or_IndPtr* при выполнении нескольких вызовов для получения данных см. в описании функции [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md). Когда данные SQL преобразуются в символьные данные C, число символов, \*возвращенное в *StrLen_or_IndPtr* , не включает байт завершения null. Если *таржетвалуептр* является пустым указателем, **SQLGETDATA** возвращает значение SQLSTATE HY009 (недопустимое использование пустого указателя). в **SQLBindCol**эта операция отменяет привязку к столбцу.  
  
 В таблицах используются следующие термины и соглашения:  
  
-   **Длина данных в байтах** — это число байтов данных C, доступных для возврата в **таржетвалуептр*, независимо от того, будут ли данные усечены перед возвратом в приложение. Для строковых данных это не включает пробел для завершающего символа null.  
  
-   **Длина байта символов** — это общее число байтов, необходимых для вывода данных в символьном формате. Это определено для каждого типа данных C в разделе [размер отображаемого](../../../odbc/reference/appendixes/display-size.md)раздела, за исключением того, что длина отображаемого байта в символах равна байтам.  
  
-   Слова в *курсиве* представляют аргументы функции или элементы грамматики SQL. Синтаксис элементов грамматики см. в [приложении C: грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Преобразование данных из SQL в C: символы](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [Преобразование данных из SQL в C: числовые данные](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [Преобразование данных из SQL в C: битовые данные](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [Преобразование данных из SQL в C: двоичные данные](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [Преобразование данных из SQL в C: даты](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [Преобразование данных из SQL в C: GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [Преобразование данных из SQL в C: время](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [Преобразование данных из SQL в C: отметки времени](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [Преобразование данных из SQL в C: интервалы месяцев года](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [Преобразование данных из SQL в C: интервалы времени дня](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [Примеры преобразования данных из SQL в C](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
