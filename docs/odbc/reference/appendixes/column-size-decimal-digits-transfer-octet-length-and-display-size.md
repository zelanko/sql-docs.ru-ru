---
title: Размер столбца, число десятичных разрядов, длительность октета передачи, отображаемый размер | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: ba21e2a13b755c938c8b1bdc321a5f23bf87c29f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213308"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Размер столбца, число десятичных разрядов, длительность октета передачи и отображаемый размер - ODBC
Типы данных характеризуются размер столбца (или параметр), десятичных цифр, длиной и размерах дисплея. Следующие функции ODBC возвращают эти атрибуты в качестве параметра в инструкции SQL или для типа данных SQL на источнике данных. Каждая функция ODBC возвращает другой набор этих атрибутов, следующим образом:  
  
-   **SQLDescribeCol** возвращает столбец, размер и дробную части числа столбцов, его описание.  
  
-   **SQLDescribeParam** возвращает параметр, размер и дробную части числа параметров, он описывает. **SQLBindParameter** задает параметр, размер и дробную части числа для параметра в инструкции SQL.  
  
-   Функции каталога **SQLColumns**, **SQLProcedureColumns**, и **SQLGetTypeInfo** возвращает атрибуты для столбца в таблице, результирующий набор или параметра процедуры и атрибуты каталога из типов данных в источнике данных. **SQLColumns** возвращает размер столбца, десятичные цифры и длину столбца в указанных таблицах (например, базовая таблица, представление или системную таблицу). **SQLProcedureColumns** возвращает размер столбца, десятичные цифры и длину столбца в процедуре. **SQLGetTypeInfo** возвращает размер столбца, максимальное и минимальное и максимальное десятичные цифры из типа данных SQL на источнике данных.  
  
 Значения, возвращаемые этими функциями для столбца или параметра размер соответствует «точность» как определенный в ODBC 2. *x*. Тем не менее значения не обязательно соответствуют значения, возвращаемые в SQL_DESC_PRECISION или других одно поле дескриптора. То же самое верно для десятичных цифр, которые соответствуют «масштаб» определено в ODBC 2. *x*. Он не обязательно соответствуют значениям, возвращаемым в SQL_DESC_SCALE или других одно поле дескриптора, но поступают из различных дескриптор поля в зависимости от типа данных. Для получения дополнительных сведений см. в разделе [размер столбца](../../../odbc/reference/appendixes/column-size.md) и [десятичных цифр](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Аналогичным образом значения для длительность октета передачи не извлекаются из SQL_DESC_LENGTH. Они берутся SQL_DESC_OCTET_LENGTH поля дескриптора для всех символьных и двоичных типов. Нет поля дескриптора, держит эту информацию для других типов.  
  
 Значение размера отображения для всех типов данных соответствует значению в поле одного дескриптора, столбцов SQL_DESC_DISPLAY_SIZE.  
  
 Поля дескриптора описывают характеристики результирующего набора. Поля дескриптора не содержат допустимых значений данных перед выполнением инструкции. Значения для столбца, размер, десятичных цифр и отобразить размер, возвращенный **SQLColumns**, **SQLProcedureColumns**, и **SQLGetTypeInfo**, с другой стороны, возвращают характеристики объектов базы данных, таких как столбцы таблицы и типы данных, которые существуют в источнике данных каталога. Аналогичным образом, в ее результирующий набор **SQLColAttribute** возвращает размер столбца, десятичные цифры и длительность октета передачи столбцов в источнике данных; эти значения не обязательно так же, как значения в SQL_DESC_PRECISION SQL_ DESC_SCALE и SQL_DESC_OCTET_LENGTH поля дескриптора.  
  
 Дополнительные сведения об этих полях дескриптора см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 См. также:  
  
-   [Размер столбца](../../../odbc/reference/appendixes/column-size.md)  
-   [Десятичные цифры](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Длительность октета передачи](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Отображаемый размер](../../../odbc/reference/appendixes/display-size.md)
