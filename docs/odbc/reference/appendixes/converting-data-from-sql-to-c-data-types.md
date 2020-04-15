---
title: Преобразование данных из S'L в Типы данных C Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284754"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Преобразование данных из SQL в типы данных C
Когда приложение вызывает **S'LFetch,** **S'LFetchScroll**, или **S'LGetData**, драйвер извлекает данные из источника данных. При необходимости он преобразует данные из типа данных, в котором драйвер получил их, в тип данных, указанный аргументом *TargetType* в **S'LBindCol** или **S'LGetData.** Наконец, он хранит данные в месте, на которое указывается аргумент *TargetValuePtr* в **S'LBindCol** или **S'LGetData** (и SQL_DESC_DATA_PTR поле ARD).  
  
 В следующей таблице показаны поддерживаемые преобразования с типов данных ODBC S'L в типы данных ODBC C. Заполненный круг указывает на конверсию по умолчанию для типа данных S'L (тип данных C, в который данные будут конвертированы, когда значение *TargetType* SQL_C_DEFAULT). Полый круг указывает на поддерживаемое преобразование.  
  
 Для приложения ODBC *3.x,* работающего с драйвером ODBC *2.x,* преобразование из типов данных, относящимся к драйверу, может не быть поддержано.  
  
 Формат преобразованных данных не зависит от настройки windows® страны.  
  
 В таблицах следующих разделов описывается, как драйвер или источник данных преобразует данные, извлеченные из источника данных; драйверы должны поддерживать конверсии во все типы данных ODBC C из поддерживаемых ими типов данных ODBC S-L. В первом столбце таблицы, для данного типа данных ODBC S'L, перечислены юридические значения ввода аргумента *TargetType* в **S'LBindCol** и **S'LGetData.** Во втором столбце перечислены результаты теста, часто используя аргумент *BufferLength,* указанный в **S'LBindCol** или **S'LGetData**, который водитель выполняет, чтобы определить, может ли он преобразовать данные. Для каждого исхода третья и четвертая столбцы перечисляют значения, помещенные в буферы, указанные *TargetValuePtr,* и *StrLen_or_IndPtr* аргументы, указанные в **S'LBindCol** или **S'LGetData** после того, как драйвер попытался преобразовать данные. (Аргумент *StrLen_or_IndPtr* соответствует SQL_DESC_OCTET_LENGTH_PTR области ARD.) В последнем столбце перечислены, что S'LSTATE возвращается для каждого исхода с **помощью S'LFetch,** **S'LFetchScroll**или **S'LGetData.**  
  
 Если аргумент *TargetType* в **S'LBindCol** или **S'LGetData** содержит идентификатор для типа данных ODBC C, не показанный в таблице для данного типа данных ODBC S'L, **S'LFetchScroll**, или **S'LGetData** возвращает S'LSTATE 07006 (нарушение атрибута типа ограниченного типа данных). **SQLFetchScroll** Если аргумент *TargetType* содержит идентификатор, который определяет преобразование из конкретного типа данных с помощью драйвера в тип данных ODBC C, и это преобразование не поддерживается драйвером, **S'LFetch,** **S'LFetchScroll**, или **S'LGetData** возвращает S'LSTATE HYC00 (необязательная функция не реализована).  
  
 Хотя он не отображается в таблицах, водитель возвращает SQL_NULL_DATA в буфер, указанный *аргументом StrLen_or_IndPtr,* когда значение данных с помощью данных NULL. Для объяснения использования *StrLen_or_IndPtr* при нескольких звонках для получения данных, см. [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md) При преобразовании данных S'L в данные символа C количество символов возвращается в \* *StrLen_or_IndPtr* не включает байт с нулевым окончанием. Если *TargetValuePtr* является нулевой указатель, **S'LGetData** возвращает S'LSTATE HY009 (Недействительное использование нулевой указатель); в **S'LBindCol**, это отвентивает столбец.  
  
 В таблицах используются следующие термины и конвенции:  
  
-   **Длина данных байт** — это количество байтов данных C, доступных для возврата в*целевом valueValuePtr,* независимо от того, будут ли данные усечены до их возврата в приложение. Для строковых данных это не включает пространство для символа с нулевым окончанием.  
  
-   **Длина байта персонажа** — это общее количество байтов, необходимых для отображения данных в формате символов. Это определено для каждого типа данных C в [разделе Размер дисплея,](../../../odbc/reference/appendixes/display-size.md)за исключением того, что длина байт-символа находится в байтах, в то время как размер дисплея находится в символах.  
  
-   Слова *курсивом* представляют собой функциональные аргументы или элементы грамматики S'L. Для синтаксиса элементов грамматики [см.](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)  
  
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
