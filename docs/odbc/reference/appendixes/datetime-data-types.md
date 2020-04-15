---
title: Типы данных на время даты (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10626c4f0bf2e33c70322a0eb49af6c3e01e4303
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307065"
---
# <a name="datetime-data-types"></a>Типы данных даты и времени
В ODBC *3.x*, идентификаторы для даты, времени и типы данных timestamp S'L изменились с SQL_DATE, SQL_TIME и SQL_TIMESTAMP (с экземплярами **#define** в файле заголовка 9, 10 и 11) до SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP (с экземплярами **#define** в файле заголовка 91, 92 и 93), соответственно. Соответствующие идентификаторы типа C изменились с SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP на SQL_C_TYPE_DATE, SQL_C_TYPE_TIME и SQL_C_TYPE_TIMESTAMP соответственно, а экземпляры **#define** соответственно изменились.  
  
 Размер столбца и десятичные цифры, возвращенные для типов данных о дате S'L в ODBC *3.x,* такие же, как точность и масштаб, возвращенные для них в ODBC *2.x.* Эти значения отличаются от значений в полях SQL_DESC_PRECISION и SQL_DESC_SCALE дескриптора. (Для получения дополнительной информации в приложении D: Типы данных [см.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
 Эти изменения влияют на **S'LDescribeCol**, **S'LDescribeParam**, и **S'LColAttributes**; **СЗЛБиндкол,** **СЗЛБандерПарастер**, и **S'LGetData**; и **S'LКолонки**, **S'LGetTypeInfo**, **S'LProcedureColumns**, **S'LСтатистика**, и **S'LSpecialКолонки**.  
  
 Драйвер ODBC *3.x* обрабатывает вызовы функции, перечисленные в предыдущем абзаце, в зависимости от настройки атрибута среды SQL_ATTR_ODBC_VERSION. Если SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3, функции возвращаются SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP в DATA_TYPE области, для **S'LColumns,** **S'LGetTypeInfo,** sLProcedures, **S'LProcedures, sLProcedures, sLProcedures, sLProcedures, sLSpecialColumns**и **S'LStatistics.** **SQLProcedureColumns** Колонка COLUMN_SIZE (в наборе результатов, возвращенном **S'LColumns,** **S'LGetTypeInfo,** **S'LProcedureColumns,** и **S'LSpecialColumns)** содержит двоичную точность для приблизительного численного типа. Колонка NUM_PREC_RADIX (в наборе результатов, возвращенном **S'LColumns,** **S'LGetTypeInfo**и **S'LProcedureColumns)** содержит значение 2. Если SQL_ATTR_ODBC_VERSION настроен на SQL_OV_ODBC2, то функции возвращаются SQL_DATE, SQL_TIME и SQL_TIMESTAMP в поле DATA_TYPE, столбец COLUMN_SIZE содержит десятичную точность для приблизительного численного типа, а столбец NUM_PREC_RADIX содержит значение 10.  
  
 При запросе всех типов данных при вызове на вызов в **S'LGetTypeInfo**набор результатов, возвращенный функцией, будет содержать как SQL_TYPE_DATE, SQL_TYPE_TIME, так и SQL_TYPE_TIMESTAMP, как это определено в ODBC *3.x,* так и SQL_DATE, SQL_TIME и SQL_TIMESTAMP, как это определено в ODBC *2.x*.  
  
 Из-за того, как менеджер драйверов ODBC *3.x* выполняет отображение типов данных даты, времени и меток времени, водителям ODBC *3.x* нужно только распознавать **#defines** 91, 92, и 93 для даты, времени и типов данных Timestamp C, введенных в аргументы *TargetType* **из S'LBindCol** и **S'LGetData** *DataType* или аргумент **SQLGetTypeInfo** *ValueType* **из S'LBindParameter**, и нужно только признать **#defines** 91, 92 и 93 для даты, времени и типа данных метки S'L, введенных в аргумент *параметр параметра* **S'LBindParameter** или Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
