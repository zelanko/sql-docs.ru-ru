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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 553596f474cd8e7c4f4c91911b0167d5b1bc0b4a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224488"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Преобразование данных из SQL в типы данных C
Если приложение вызывает **SQLFetch**, **SQLFetchScroll**, или **SQLGetData**, драйвер получает данные из источника данных. При необходимости, она преобразует данные из типа данных, в котором драйвер получены его тип данных, указанный в *TargetType* аргумента в **SQLBindCol** или **SQLGetData.** Наконец, он сохраняет данные в расположении, указанном *TargetValuePtr* аргумента в **SQLBindCol** или **SQLGetData** (и поле SQL_DESC_DATA_PTR Отменить).  
  
 Ниже приведены поддерживаемые преобразования типов ODBC SQL типы данных в типы данных C в ODBC. Заполненный круг указывает преобразования по умолчанию для типа данных SQL (тип данных C, к которому данные будут преобразованы когда значение *TargetType* — SQL_C_DEFAULT). Пустой круг указывает преобразование поддерживается.  
  
 Для ODBC 3 *.x* приложение, которое работает с ODBC 2. *x* драйвер, преобразование из данных типов могут не поддерживаться.  
  
 Формат данных, преобразованный в параметр страны Windows® не повлияет.  
  
 В таблицах в следующих разделах описано, как драйверу или источнику данных преобразует данные, полученные из источника данных. драйверы необходимы для поддержки преобразования типов данных ODBC C из типов данных ODBC SQL, которые они поддерживают. Для данного типа данных ODBC SQL, в первом столбце таблицы перечислены допустимые входные значения *TargetType* аргумента в **SQLBindCol** и **SQLGetData**. Во втором столбце перечислены результаты теста, часто с помощью *BufferLength* аргумент, указанный в **SQLBindCol** или **SQLGetData**, выполняющий драйвер для Определите, может ли преобразование данных. Для каждого результата, третий и четвертый столбцы список значений, помещаются в буферах, определяемое *TargetValuePtr* и *StrLen_or_IndPtr* аргументов, указанных в **SQLBindCol** или **SQLGetData** после драйвер попытался преобразовать данные. ( *StrLen_or_IndPtr* аргумент соответствует поле SQL_DESC_OCTET_LENGTH_PTR Отменить.) Последний столбец перечислены SQLSTATE, возвращаемых для каждого результата с **SQLFetch**, **SQLFetchScroll**, или **SQLGetData**.  
  
 Если *TargetType* аргумента в **SQLBindCol** или **SQLGetData** содержит идентификатор для типа данных ODBC C, не показаны в таблице для данного типа данных ODBC SQL,  **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** возвращает SQLSTATE 07006 (нарушение ограниченного типа данных атрибута). Если *TargetType* аргумент содержит идентификатор, который определяет преобразование из типа данных SQL, относящиеся к драйверу к типу данных ODBC C, и это преобразование не поддерживается драйвером, **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** возвращает SQLSTATE HYC00 (дополнительная возможность не реализована).  
  
 Несмотря на то, что это не показано в таблицах, драйвер возвращает SQL_NULL_DATA в буфере, определяемое *StrLen_or_IndPtr* аргумент, если значение данных SQL имеет значение NULL. Описание использования *StrLen_or_IndPtr* при нескольких вызовов для получения данных, см. в разделе [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)описание функции. Возвращается при преобразовании данных SQL в символьный C количество символов в \* *StrLen_or_IndPtr* не включает байтов конечное значение null. Если *TargetValuePtr* является пустым указателем, **SQLGetData** возвращает SQLSTATE HY009 (недопустимое использование пустого указателя), в списке **SQLBindCol**, это отменяется привязка значения столбца.  
  
 В таблицах используются следующие условия и соглашения.  
  
-   **Байтовая длина данных** — количество байтов, доступных для возврата данных C **TargetValuePtr*независимо от того, данные будут усечены до его возврата в приложение или нет. Для строковых данных это не включает место для символа завершения null.  
  
-   **Длина байтов символьной** — общее количество байтов, необходимое для отображения данных в символьном формате. Это, как определено для каждого типа данных C в разделе [отображения размер](../../../odbc/reference/appendixes/display-size.md), за исключением того, что символ байт находится в байтах, а размер экрана в символы.  
  
-   Ключевые слова в *курсив* представляют аргументы функции или элементы в грамматику SQL. Синтаксис элементов грамматики, см. в разделе [приложение в: Грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [SQL в C: Символ](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL в C: Numeric](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL в C: Бит](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL в C: Двоичный](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL в C: Дата](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL в C: ИДЕНТИФИКАТОР GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL в C: время](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL в C: Метка времени](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL в C: Интервалы месяцев года](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL в C: Интервалы времени дня](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [Примеры преобразования данных из SQL в C](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
