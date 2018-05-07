---
title: Преобразование данных из SQL в типы данных C | Документы Microsoft
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 370286bb4e955247e53d3c010b0bbb2088957bbe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Преобразование данных из SQL в типы данных C
Если приложение вызывает **SQLFetch**, **SQLFetchScroll**, или **SQLGetData**, драйвер получает данные из источника данных. Если необходимо, оно преобразует данные из типа данных, в котором драйвер выборки его тип данных, указанный в *TargetType* аргумент в **SQLBindCol** или **SQLGetData.** Наконец, данные сохраняются в расположении, указанном *TargetValuePtr* аргумент в **SQLBindCol** или **SQLGetData** (и поле SQL_DESC_DATA_PTR Отменить).  
  
 Следующая таблица показывает поддерживаемые преобразования типов ODBC SQL типы данных в типы данных ODBC C. Указывает, заполненный круг преобразования по умолчанию для типа данных SQL (тип данных C, в котором данные будет преобразован при значение *TargetType* — SQL_C_DEFAULT). Полый круг указывает поддерживаемые преобразования.  
  
 Для ODBC 3 *.x* приложения, работа с ODBC 2. *x* драйвера, преобразование из данных типы не поддерживаются.  
  
 Формат преобразованных данных не влияют параметры Windows® страны.  
  
 В таблицах в следующих разделах описано, как драйверу или источнику данных преобразует данные, полученные из источника данных. необходимые драйверы для поддержки преобразований во все типы данных ODBC C в типы данных ODBC SQL, которые они поддерживают. Для данного типа данных ODBC SQL, в первом столбце таблицы перечислены допустимые входные значения *TargetType* аргумент в **SQLBindCol** и **SQLGetData**. Во втором столбце перечислены результаты теста, часто с помощью *BufferLength* аргумент, указанный в **SQLBindCol** или **SQLGetData**, что драйвер выполняет Определите, может ли преобразовать данные. Для каждого результата, третий и четвертый столбцы перечислены значения, помещаются в буферах, определяемое *TargetValuePtr* и *StrLen_or_IndPtr* аргументы, заданные в **SQLBindCol** или **SQLGetData** после драйвер попытался преобразовать данные. ( *StrLen_or_IndPtr* аргумент соответствует поле SQL_DESC_OCTET_LENGTH_PTR Отменить.) Последний столбец перечислены SQLSTATE, возвращенное для каждого результата с **SQLFetch**, **SQLFetchScroll**, или **SQLGetData**.  
  
 Если *TargetType* аргумент в **SQLBindCol** или **SQLGetData** содержит идентификатор для типа данных ODBC C, не отображаются в таблице для данного типа данных ODBC SQL,  **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** возвращает SQLSTATE 07006 (нарушение ограниченного типа данных атрибута). Если *TargetType* аргумент содержит идентификатор, который указывает преобразование из типа данных, относящиеся к драйверу SQL в тип данных ODBC C и данное преобразование не поддерживается драйвером, **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** возвращает SQLSTATE HYC00 (дополнительная возможность не реализована).  
  
 Несмотря на то, что он не содержится в таблицах, драйвер возвращает в указанный буфер SQL_NULL_DATA *StrLen_or_IndPtr* аргумента при SQL данные имеют значение NULL. Описание использования *StrLen_or_IndPtr* при несколько вызовов, выполняемых для извлечения данных, в разделе [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)описание функции. При преобразовании данных SQL в C символьные данные, возвращаемое число символов в \* *StrLen_or_IndPtr* не включает байтов конечное значение null. Если *TargetValuePtr* является пустым указателем, **SQLGetData** возвращает SQLSTATE HY009 (недопустимое использование пустого указателя); в **SQLBindCol**, это отменяется привязка значения столбца.  
  
 В таблицах используются следующие термины и соглашения.  
  
-   **Байтовая длина данных** число байтов, доступных для возврата данных C **TargetValuePtr*независимо от того, данные будут усечены до его возврата в приложение или нет. Для строковых данных это не учитывает пространство для знака завершения null.  
  
-   **Длина байтов символьной** — общее количество байтов, необходимое для отображения данных в символьном формате. Это, как определено для каждого типа данных C в разделе [размер отображения](../../../odbc/reference/appendixes/display-size.md), за исключением того, что байт символа находится в байтах, а размер экрана в символы.  
  
-   Слова в *курсив* представляют аргументы функции или элементы грамматику SQL. Синтаксис элементов грамматики см [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
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
