---
title: Преобразование данных с C в типы данных S-L Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304663"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Преобразование данных из C в типы данных SQL
Когда приложение вызывает **S'LExecute** или **S'LExecDirect,** драйвер получает данные по любым параметрам, связанным с **S'LBindParameter** из мест хранения в приложении. При вызове приложения **s'LSetPos**драйвер получает данные для обновления или добавления операции из столбцов, связанных с **S'LBindCol.** Для параметров данных по исполнению приложение отправляет данные параметров с **помощью S'LPutData.** При необходимости драйвер преобразует данные из типа данных, указанного аргументом *ValueType* в **sLBindParameter,** в тип данных, указанный аргументом *ParameterType,* в **S'LBindParameter,** а затем отправляет данные в источник данных.  
  
 В следующей таблице показаны поддерживаемые преобразования с типов данных ODBC C в типы данных ODBC S'L. Заполненный круг указывает на конверсию по умолчанию для типа данных S'L (тип данных C, из которого данные будут конвертированы при SQL_C_DEFAULT значения *ValueType* или SQL_DESC_CONCISE_TYPE дескриптора). Полый круг указывает на поддерживаемое преобразование.  
  
 Формат преобразованных данных не зависит от настройки windows® страны.  
  
 ![Поддерживаемые преобразования: ODBC C в SQL типы данных](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 В таблицах следующих разделов описывается, как драйвер или источник данных преобразует данные, отправленные в источник данных; драйверы должны поддерживать переходы от всех типов данных ODBC C к поддерживаемым ими типам данных ODBC S'L. Для данного типа данных ODBC C в первом столбце таблицы перечислены юридические значения ввода аргумента *ParameterType* в **S'LBindParameter.** Во втором столбце перечислены результаты теста, который выполняет драйвер для определения того, может ли он преобразовать данные. В третьей колонке перечислены, что S'LSTATE, возвращенные для каждого исхода, по **s'LExecDirect,** **S'LExecute,** **S'LBulkOperations**, **S'LSetPos**, или **S'LPutData**. Данные отправляются в источник данных только в SQL_SUCCESS возвращается.  
  
 Если аргумент *ParameterTypeType* в **S'LBindParameter** содержит идентификатор типа данных ODBC S'L, который не отображается в таблице для данного типа данных C, **S'LBindParameter** возвращает S'LSTATE 07006 (нарушение атрибута типа ограниченного типа данных). Если аргумент *ParameterTypeType* содержит идентификатор конкретного драйвера и драйвер не поддерживает преобразование из конкретного типа данных ODBC C в этот тип данных, специфичный для драйверов, **S'LBindParameter** возвращает S'LSTATE HYC00 (необязательная функция не реализована).  
  
 Если *ПараметрВалутптр* и *StrLen_or_IndPtr* аргументы, указанные в **S'LBindParameter,** являются нулевыми указателями, эта функция возвращает S'LSTATE HY009 (недействительное использование нулевого указателя). Хотя это не показано в таблицах, приложение устанавливает значение буфера длины/индикатора, на который указывает *StrLen_or_IndPtr* аргумент **s'LBindParameter** или значение *StrLen_or_IndPtr* **аргумента S'LPutData,** чтобы SQL_NULL_DATA указать значение данных NULL S'L. (Аргумент *StrLen_or_IndPtr* соответствует SQL_DESC_OCTET_LENGTH_PTR области APD.) Приложение \*устанавливает эти значения, чтобы SQL_NTS указать, что значение в *ParameterValuePtr* в **S'LBindParameter** или \* *DataPtr* в **S'LPutData** (указывается на SQL_DESC_DATA_PTR поле APD) является нулевым завершена строка.  
  
 В таблицах используются следующие термины:  
  
-   **Длина данных байт** - Количество байтов данных СЗЛ, доступных для отправки в источник данных, будут ли данные усечены до их отправки в источник данных. Для строковых данных это не включает место для символа с нулевым окончанием.  
  
-   **Длина столбца байт** - Количество байтов, необходимых для хранения данных в источнике данных.  
  
-   **Длина байта персонажа** - Максимальное количество байтов, необходимых для отображения данных в форме персонажа. Это определено для каждого типа данных S'L в [размере дисплея,](../../../odbc/reference/appendixes/display-size.md)за исключением длины байта символа находится в байтах, в то время как размер дисплея находится в символах.  
  
-   **Количество цифр** - Количество символов, используемых для представления числа, включая знак минус, десятичную точку и показатель (при необходимости).  
  
-   **Слова в**   
     ***курсивом*** - Элементы грамматики S'L. Для синтаксиса элементов грамматики [см.](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)  
  
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
