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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aca333a6f3006b1f12cf44d1670e38556027e476
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019118"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Преобразование данных из C в типы данных SQL
Если приложение вызывает **SQLExecute** или **SQLExecDirect**, драйвер получает данные для параметров, привязанного с **SQLBindParameter** из места хранения в приложение. Если приложение вызывает **SQLSetPos**, драйвер получает данные для обновления или операции добавления столбцов, привязанных с **SQLBindCol**. Для параметров данных времени выполнения, приложение отправляет данные с помощью параметра **SQLPutData**. Если необходимо, драйвер преобразует данные из типа данных, указанного *ValueType* аргумента в **SQLBindParameter** тип данных, указанный в *ParameterType*аргумента в **SQLBindParameter**, а затем отправляет данные в источник данных.  
  
 Ниже приведены также поддерживаемое преобразование из C в ODBC типы данных в типы данных ODBC SQL. Заполненный круг указывает преобразования по умолчанию для типа данных SQL (тип данных C, из которого данные будут преобразованы когда значение *ValueType* или поле дескриптора SQL_DESC_CONCISE_TYPE является SQL_C_DEFAULT). Пустой круг указывает преобразование поддерживается.  
  
 Формат данных, преобразованный в параметр страны Windows® не повлияет.  
  
 ![Поддерживаемые преобразования: ODBC C в типы данных SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 В таблицах в следующих разделах описано, как драйверу или источнику данных преобразует данные, отправляемые в источник данных; драйверы необходимы для поддержки преобразования типов данных ODBC C в типы данных ODBC SQL, которые они поддерживают. Для данного типа данных ODBC C, в первом столбце таблицы перечислены допустимые входные значения *ParameterType* аргумента в **SQLBindParameter**. Во втором столбце перечислены результаты теста, который выполняет драйвер для определения, если он может преобразовать данные. В третьем столбце представлены SQLSTATE, возвращаемых для каждого результата с **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**, или **SQLPutData**. Данные отправляются в источник данных только в том случае, если возвращается значение SQL_SUCCESS.  
  
 Если *ParameterType* аргумента в **SQLBindParameter** содержит идентификатор типа данных ODBC SQL, не содержится в таблице для данного типа данных C, **SQLBindParameter**возвращает SQLSTATE 07006 (нарушение ограниченного типа данных атрибута). Если *ParameterType* аргумент содержит идентификатор конкретного драйвера, и драйвер не поддерживает преобразование из типа данных ODBC C в этот тип данных специфические для драйвера SQL **SQLBindParameter** возвращает SQLSTATE HYC00 (дополнительная возможность не реализована).  
  
 Если *ParameterValuePtr* и *StrLen_or_IndPtr* аргументов, указанных в **SQLBindParameter** являются оба пустыми указателями, что функция возвращает SQLSTATE HY009 (недопустимый использование пустого указателя). Несмотря на то, что это не показано в таблицах, приложение задает значение буфера длины и индикатора, *StrLen_or_IndPtr* аргумент **SQLBindParameter** или значение  *StrLen_or_IndPtr* аргумент **SQLPutData** в значение SQL_NULL_DATA для указания значения данных NULL SQL. ( *StrLen_or_IndPtr* аргумент соответствует поле SQL_DESC_OCTET_LENGTH_PTR в APD.) Приложение задает эти значения для SQL_NTS, чтобы указать, что значение в \* *ParameterValuePtr* в **SQLBindParameter** или \* *DataPtr*в **SQLPutData** (на него указывает поле SQL_DESC_DATA_PTR в APD) — это строка с завершающим нулем.  
  
 В таблицах используются следующие термины:  
  
-   **Байтовая длина данных** — число байтов данных SQL может отправлять к источнику данных, ли данные будут усечены перед их отправкой к источнику данных. Для строковых данных это не включает место для символа завершения null.  
  
-   **Длина столбца байтов** -число байтов, необходимое для хранения данных в источнике данных.  
  
-   **Длина байтов символьной** — максимальное число байтов, чтобы отобразить данные в виде символа. Это, как определено для каждого типа данных SQL в [отображения размер](../../../odbc/reference/appendixes/display-size.md), за исключением, что символ байт находится в байтах, а размер экрана в символы.  
  
-   **Число цифр или символов** — число символов, используемых для представления числа, включая знак минуса, десятичной запятой и показатель степени (при необходимости).  
  
-   **Слова в**   
     ***Курсив*** -элементы грамматики SQL. Синтаксис элементов грамматики, см. в разделе [приложение в: Грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Преобразование из C в SQL: Символ](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [Преобразование из C в SQL: Numeric](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [Преобразование из C в SQL: Бит](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [Преобразование из C в SQL: Двоичный](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [Преобразование из C в SQL: Дата](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [Преобразование из C в SQL: ИДЕНТИФИКАТОР GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [Преобразование из C в SQL: время](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [Преобразование из C в SQL: Метка времени](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [Преобразование из C в SQL: Интервалы месяцев года](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [Преобразование из C в SQL: Интервалы времени дня](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Примеры преобразования данных из C в SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
