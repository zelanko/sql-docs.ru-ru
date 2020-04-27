---
title: Преобразование данных из C в типы данных SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], about converting
- converting data from c to SQL types [ODBC]
- data conversions from C to SQL types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- SQL data types [ODBC], converting from C types
- data types [ODBC], SQL data types
- data conversions from C to SQL types [ODBC]
- C data types [ODBC], converting to SQL types
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8fb707e77df7d793277d4a23146adc980eede6fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304663"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Преобразование данных из C в типы данных SQL
Когда приложение вызывает **SQLExecute** или **SQLExecDirect**, драйвер получает данные для всех параметров, привязанных к **SQLBindParameter** из мест хранения в приложении. Когда приложение вызывает функцию **SQLSetPos**, драйвер получает данные для операции обновления или добавления из столбцов, привязанных к **SQLBindCol**. Для параметров, выполняемых при выполнении данных, приложение отправляет данные параметров с помощью **SQLPutData**. При необходимости драйвер преобразует данные из типа данных, указанного аргументом *ValueType* в **SQLBindParameter** , в тип данных, указанный аргументом *ParameterType* в **SQLBindParameter**, а затем отправляет данные в источник данных.  
  
 В следующей таблице приведены поддерживаемые преобразования типов данных ODBC C в типы данных ODBC SQL. Заполненный круг обозначает преобразование по умолчанию для типа данных SQL (тип данных C, из которого будут преобразованы данные, если значение *ValueType* или поле дескриптора SQL_DESC_CONCISE_TYPE SQL_C_DEFAULT). Пустой кружок обозначает поддерживаемое преобразование.  
  
 Формат преобразованных данных не зависит от параметра Country® Windows.  
  
 ![Поддерживаемые преобразования: ODBC C в SQL типы данных](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 В таблицах в следующих разделах описывается, как драйвер или источник данных преобразуют данные, отправляемые в источник данных. драйверы необходимы для поддержки преобразований из всех типов данных ODBC C в типы данных ODBC SQL, которые они поддерживают. Для данного типа данных ODBC C в первом столбце таблицы перечислены допустимые входные значения аргумента *ParameterType* в **SQLBindParameter**. Во втором столбце перечислены результаты теста, выполняемого драйвером, чтобы определить, может ли он преобразовать данные. В третьем столбце содержится значение SQLSTATE, возвращенное для каждого результата, по **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**или **SQLPutData**. Данные отправляются в источник данных только при возвращении SQL_SUCCESS.  
  
 Если аргумент *ParameterType* в **SQLBindParameter** содержит идентификатор типа данных ODBC SQL, который не показан в таблице для данного типа данных C, **SQLBindParameter** возвращает значение SQLSTATE 07006 (нарушение атрибута ограниченного типа данных). Если аргумент *ParameterType* содержит идентификатор, зависящий от драйвера, и драйвер не поддерживает преобразование из определенного типа данных ODBC C в этот тип данных SQL конкретного драйвера, **SQLBINDPARAMETER** возвращает значение SQLSTATE HYC00 (дополнительная функция не реализована).  
  
 Если аргументы *параметервалуептр* и *StrLen_or_IndPtr* , указанные в **SQLBindParameter** , являются пустыми указателями, эта функция возвращает значение SQLSTATE HY009 (недопустимое использование указателя NULL). Хотя он не показан в таблицах, приложение устанавливает значение буфера длины или индикатора, на которое указывает аргумент *StrLen_or_IndPtr* **SQLBindParameter** , или значение *StrLen_or_IndPtr* аргумента **SQLPutData** в SQL_NULL_DATA, чтобы указать значение данных SQL NULL. (Аргумент *StrLen_or_IndPtr* соответствует полю SQL_DESC_OCTET_LENGTH_PTR объекта APD.) Приложение устанавливает эти значения в SQL_NTS, чтобы указать, что значение в \* *параметервалуептр* в **SQLBindParameter** или \* *датаптр* в **SQLPutData** (на которое указывает SQL_DESC_DATA_PTR поле APD) является строкой, завершающейся нулем.  
  
 В таблицах используются следующие термины:  
  
-   **Байтовая длина данных** — количество байт данных SQL, доступных для отправки в источник данных, независимо от того, будут ли данные усечены перед отправкой в источник данных. Для строковых данных это не включает пробел для завершающего символа null.  
  
-   **Длина байта столбца** — число байтов, необходимое для хранения данных в источнике данных.  
  
-   **Длина байта символов** — максимальное число байтов, необходимое для вывода данных в символьной форме. Это определено для каждого типа данных SQL в [отображаемом размере](../../../odbc/reference/appendixes/display-size.md), за исключением того, что длина байтовой кодировки равна байтам, а отображаемый размер — в символах.  
  
-   **Количество цифр** — число символов, используемых для представления числа, включая знак минуса, десятичную запятую и экспоненту (при необходимости).  
  
-   **Слова в**   
     ***курсив*** — элементы грамматики SQL. Синтаксис элементов грамматики см. в [приложении C: грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Преобразование из C в SQL: символы](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [Преобразование из C в SQL: числовые данные](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [Преобразование из C в SQL: битовые данные](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [Преобразование из C в SQL: двоичные данные](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [Преобразование из C в SQL: даты](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [Преобразование из C в SQL: GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [Преобразование из C в SQL: время](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [Преобразование из C в SQL: отметки времени](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [Преобразование из C в SQL: интервалы месяцев года](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [Преобразование из C в SQL: интервалы времени дня](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Примеры преобразования данных из C в SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
