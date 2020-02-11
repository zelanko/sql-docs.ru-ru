---
title: Изменения типа данных DateTime | Документация Майкрософт
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
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6bc7e07ab65b5894c3ac2b913e5d4afcbd4f98f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076964"
---
# <a name="datetime-data-type-changes"></a>Изменения в типе данных Datetime
В ODBC *3. x*идентификаторы типов данных SQL даты, времени и timestamp изменились с SQL_DATE, SQL_TIME и SQL_TIMESTAMP (с экземплярами **#define** в файле заголовка 9, 10 и 11) на SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP (с экземплярами **#define** в файле заголовка 91, 92 и 93) соответственно. Соответствующие идентификаторы типа C изменились с SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP на SQL_C_TYPE_DATE, SQL_C_TYPE_TIME и SQL_C_TYPE_TIMESTAMP соответственно.  
  
 Размер столбца и десятичные цифры, возвращаемые для типов данных SQL datetime в ODBC *3. x* , совпадают с точностью и масштабом, возвращаемым для них в ODBC *2. x*. Эти значения отличаются от значений в полях дескриптора SQL_DESC_PRECISION и SQL_DESC_SCALE. (Дополнительные сведения см. в разделе [размер столбца, десятичные цифры, длина октета и размер отображаемого](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)данных.)  
  
 Эти изменения влияют на **SQLDescribeCol**, **SQLDescribeParam**и **SQLColAttribute**; **SQLBindCol**, **SQLBindParameter**и **SQLGetData**; и **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLStatistics**и **SQLSpecialColumns**.  
  
 В следующей таблице показано, как диспетчер драйверов ODBC *3. x* выполняет сопоставление типов данных даты, времени и меток времени C, вводимых в аргументах *TargetType* **SQLBindCol** и **SQLGetData** , или в аргументе *ValueType* **SQLBindParameter**.  
  
|Тип данных<br /><br /> код добавлен|Приложение *2. x*<br /><br /> драйвер *2. x*|Приложение *2. x*<br /><br /> драйвер *3. x*|Приложение *3. x*<br /><br /> драйвер *2. x*|Приложение *3. x*<br /><br /> драйвер *3. x*|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Нет сопоставления|SQL_C_TYPE_DATE (91)|Без сопоставления [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Ошибка (из DM)|Ошибка (из DM)|SQL_C_DATE (9)|Без сопоставления [2]|  
|SQL_C_TIME (10)|Нет сопоставления|SQL_C_TYPE_TIME (92)|Без сопоставления [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Ошибка (из DM)|Ошибка (из DM)|SQL_C_TIME (10)|Без сопоставления [2]|  
|SQL_C_TIMESTAMP (11)|Нет сопоставления|SQL_C_TYPE_TIMESTAMP (93)|Без сопоставления [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Ошибка (из DM)|Ошибка (из DM)|SQL_C_TIMESTAMP (11)|Без сопоставления [2]|  
  
 [1] в результате приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , может использовать коды даты, времени или отметки времени, возвращенные в результирующих наборах, возвращаемых функциями каталога.  
  
 [2] в результате приложение ODBC *3. x* , работающее с драйвером ODBC *3. x* , может использовать даты, время или коды меток времени, возвращенные в результирующих наборах, возвращаемых функциями каталога.  
  
 В следующей таблице показано, как диспетчер драйверов ODBC *3. x* выполняет сопоставление типов данных даты, времени и МЕТОК времени SQL, вводимых в аргументе *ParameterType* **SQLBindParameter** , или в аргументе *DataType* объекта **SQLGetTypeInfo**.  
  
|Тип данных<br /><br /> код добавлен|Приложение *2. x*<br /><br /> драйвер *2. x*|Приложение *2. x*<br /><br /> драйвер *3. x*|Приложение *3. x*<br /><br /> драйвер *2. x*|Приложение *3. x*<br /><br /> драйвер *3. x*|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Нет сопоставления|SQL_TYPE_DATE (91)|Без сопоставления [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Ошибка (из DM)|Ошибка (из DM)|SQL_DATE (9)|Без сопоставления [2]|  
|SQL_TIME (10)|Нет сопоставления|SQL_TYPE_TIME (92)|Без сопоставления [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Ошибка (из DM)|Ошибка (из DM)|SQL_TIME (10)|Без сопоставления [2]|  
|SQL_TIMESTAMP (11)|Нет сопоставления|SQL_TYPE_TIMESTAMP (93)|Без сопоставления [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Ошибка (из DM)|Ошибка (из DM)|SQL_TIMESTAMP (11)|Без сопоставления [2]|  
  
 [1] в результате приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , может использовать коды даты, времени или отметки времени, возвращенные в результирующих наборах, возвращаемых функциями каталога.  
  
 [2] в результате приложение ODBC *3. x* , работающее с драйвером ODBC *3. x* , может использовать даты, время или коды меток времени, возвращенные в результирующих наборах, возвращаемых функциями каталога.
