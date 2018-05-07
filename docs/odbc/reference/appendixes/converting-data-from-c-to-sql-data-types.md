---
title: Преобразование данных из C в типы данных SQL | Документы Microsoft
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
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f08f4294b5b6c44c54d9f577ec423f7d298181a0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Преобразование данных из C в типы данных SQL
Если приложение вызывает **SQLExecute** или **SQLExecDirect**, драйвер получает данные для любой параметры связаны с **SQLBindParameter** из места хранения в приложение. Если приложение вызывает **SQLSetPos**, драйвер извлекает данные для обновления или операции добавления столбцов, привязанных с **SQLBindCol**. Для параметров данных во время выполнения приложение отправляет данные параметра с **SQLPutData**. Если необходимо, драйвер преобразует данные из типа данных, указанного *ValueType* аргумент в **SQLBindParameter** тип данных, указанный в *ParameterType*аргумент в **SQLBindParameter**, а затем отправляет данные в источник данных.  
  
 Следующая таблица показывает поддерживаемые преобразования из C в ODBC типов данных в типы данных ODBC SQL. Указывает, заполненный круг преобразования по умолчанию для типа данных SQL (тип данных C, из которого данные преобразуются при значение *ValueType* или поле дескриптора SQL_DESC_CONCISE_TYPE является SQL_C_DEFAULT). Полый круг указывает поддерживаемые преобразования.  
  
 Формат преобразованных данных не влияют параметры Windows® страны.  
  
 ![Поддерживаемые преобразования: ODBC C в типы данных SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 В таблицах в следующих разделах описано, как драйверу или источнику данных преобразует данные, отправляемые в источнике данных; необходимые драйверы для поддержки преобразования типов данных ODBC C в типы данных ODBC SQL, которые они поддерживают. Для данного типа данных ODBC C, в первом столбце таблицы перечислены допустимые входные значения *ParameterType* аргумент в **SQLBindParameter**. Во втором столбце перечислены результаты теста, который выполняет драйвер для определения, если он может преобразовать данные. В третьем столбце представлены SQLSTATE, возвращенное для каждого результата с **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**, или **SQLPutData**. Данные отправляются в источник данных только в том случае, если возвращается значение SQL_SUCCESS.  
  
 Если *ParameterType* аргумент в **SQLBindParameter** содержит идентификатор типа данных ODBC SQL, который не содержится в таблице для данного типа данных C, **SQLBindParameter**возвращает SQLSTATE 07006 (нарушение ограниченного типа данных атрибута). Если *ParameterType* аргумент содержит идентификатор драйвера и драйвер не поддерживает преобразование из определенного типа данных ODBC C к типу данных SQL, относящиеся к драйверу **SQLBindParameter** возвращает SQLSTATE HYC00 (дополнительная возможность не реализована).  
  
 Если *ParameterValuePtr* и *StrLen_or_IndPtr* аргументы, заданные в **SQLBindParameter** — оба неопределенные указатели, что функция возвращает SQLSTATE HY009 (не допускается использование пустого указателя). Несмотря на то, что он не содержится в таблицах, приложение задает значение буфера длины и индикатора, *StrLen_or_IndPtr* аргумент **SQLBindParameter** или значение  *StrLen_or_IndPtr* аргумент **SQLPutData** значение SQL_NULL_DATA для указания значения данных NULL SQL. ( *StrLen_or_IndPtr* аргумент соответствует поле SQL_DESC_OCTET_LENGTH_PTR в APD.) Приложение устанавливает эти значения для SQL_NTS, чтобы указать, что значение в \* *ParameterValuePtr* в **SQLBindParameter** или \* *DataPtr*в **SQLPutData** (ссылается поле SQL_DESC_DATA_PTR в APD) представляет собой строку, завершающуюся значением null.  
  
 В таблицах используются следующие термины:  
  
-   **Байтовая длина данных** — число байтов данных SQL для отправки в источник данных, независимо от того, имеется ли данные будут усечены, перед отправкой к источнику данных. Для строковых данных это не учитывает пространство для знака завершения null.  
  
-   **Длина столбца в байтах** — число байтов, необходимое для хранения данных в источнике данных.  
  
-   **Длина байтов символьной** — максимальное число байтов, необходимое для отображения данных в виде символа. Это, как это определено для каждого типа данных SQL в [размер отображения](../../../odbc/reference/appendixes/display-size.md), за исключением байт символа находится в байтах, а размер экрана в символы.  
  
-   **Число цифр** — количество символов, используемых для представления чисел, включая знак «минус», десятичного разделителя и показатель степени (при необходимости).  
  
-   **Слова в**   
     ***Курсив*** — элементы грамматику SQL. Синтаксис элементов грамматики см [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
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
