---
title: Размер столбца, десятичные цифры, длина октета, размер дисплея | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- data types [ODBC], column size
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
- data types [ODBC], transfer octet length
ms.assetid: 723107a1-be08-4ea3-a8c0-b2c45d38d1aa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d8d7f1b8ec5647a34b09f0636fc8fcc2ad070f72
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019242"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Размер столбца, десятичные цифры, длина октета и размер дисплея — ODBC
Типы данных характеризуются размером столбца (или параметра), десятичными цифрами, длиной и отображаемым размером. Следующие функции ODBC возвращают эти атрибуты для параметра в инструкции SQL или для типа данных SQL в источнике данных. Каждая функция ODBC возвращает различные наборы этих атрибутов следующим образом.  
  
-   **SQLDescribeCol** возвращает размер столбца и десятичные цифры столбцов, которые он описывает.  
  
-   **SQLDescribeParam** возвращает размер параметра и десятичные разряды параметров, которые он описывает. **SQLBindParameter** задает размер параметра и десятичные цифры для параметра в инструкции SQL.  
  
-   Функции каталога **SQLColumns**, **SQLProcedureColumns**и **SQLGetTypeInfo** возвращают атрибуты для столбца в таблице, результирующего набора или параметра процедуры и атрибутов каталога типов данных в источнике данных. **SQLColumns** возвращает размер столбца, десятичные цифры и длину столбца в указанных таблицах (например, базовая таблица, представление или системная таблица). **SQLProcedureColumns** возвращает размер столбца, десятичные цифры и длину столбца в процедуре. **SQLGetTypeInfo** Возвращает максимальный размер столбца и минимальное и максимальное десятичные разряды типа данных SQL в источнике данных.  
  
 Значения, возвращаемые этими функциями для размера столбца или параметра, соответствуют «Precision», как определено в ODBC 2. *x*. Однако значения не обязательно соответствуют значениям, возвращаемым в SQL_DESC_PRECISION или любом другом поле дескриптора. Это справедливо и для десятичных цифр, соответствующих "Scale", как определено в ODBC 2. *x*. Он не обязательно соответствует значениям, возвращаемым в SQL_DESC_SCALE или любом другом поле дескриптора, но поступает из разных полей дескриптора в зависимости от типа данных. Дополнительные сведения см. в разделе [размер столбца](../../../odbc/reference/appendixes/column-size.md) и [десятичные цифры](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Аналогичным образом значения для длины октета не берутся из SQL_DESC_LENGTH. Они берутся из SQL_DESC_OCTET_LENGTH поля дескриптора для всех символьных и двоичных типов. Отсутствует поле дескриптора, содержащее эти сведения для других типов.  
  
 Значение отображаемого размера для всех типов данных соответствует значению в одном поле дескриптора SQL_DESC_DISPLAY_SIZE.  
  
 Поля дескриптора описывают характеристики результирующего набора. Поля дескриптора не содержат допустимых значений данных перед выполнением инструкции. Значения размера столбца, десятичных знаков и размера отображения, возвращаемых **SQLColumns**, **SQLProcedureColumns**и **SQLGetTypeInfo**, с другой стороны, возвращают характеристики объектов базы данных, такие как столбцы таблицы и типы данных, которые существуют в каталоге источника данных. Аналогичным образом в результирующем наборе **SQLColAttribute** возвращает размер столбца, десятичные цифры и длину октета для столбцов в источнике данных. Эти значения не обязательно должны совпадать со значениями в полях дескриптора SQL_DESC_PRECISION, SQL_DESC_SCALE и SQL_DESC_OCTET_LENGTH.  
  
 Дополнительные сведения об этих полях дескрипторов см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Связанные разделы:  
  
-   [Размер столбца](../../../odbc/reference/appendixes/column-size.md)  
-   [Десятичные цифры](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Длительность октета передачи](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Отображаемый размер](../../../odbc/reference/appendixes/display-size.md)
