---
title: "Размер столбца, десятичных цифр, длина в октетах передачи объем | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19f505751d63f07dbd5eb2d1d53b9c191307e9b2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Размер столбца, десятичных цифр, передачи длина в октетах и размер - ODBC
Типы данных характеризуются их размер столбца (или параметр), десятичных цифр, длина и размер изображения. Следующие функции ODBC возвращают эти атрибуты в качестве параметра в инструкции SQL или для типа данных SQL на источнике данных. Каждая функция ODBC возвращает набор этих атрибутов следующим образом:  
  
-   **SQLDescribeCol** возвращает размер и дробную части числа столбцов, он описывает столбец.  
  
-   **SQLDescribeParam** возвращает размер и дробную части числа параметров, он описывает параметр. **SQLBindParameter** задает размер и дробную части числа для параметра для параметра в инструкции SQL.  
  
-   Функции каталогов **SQLColumns**, **SQLProcedureColumns**, и **SQLGetTypeInfo** возвращает атрибуты для столбца в таблице, результирующий набор или параметра процедуры и атрибуты каталога типов данных в источнике данных. **SQLColumns** возвращает размер столбца, десятичные цифры и длину столбца в указанных таблицах (например, базовая таблица, представление или системной таблицы). **SQLProcedureColumns** возвращает размер столбца, десятичные цифры и длину столбца в процедуре. **SQLGetTypeInfo** возвращает размер столбца, максимальное и минимальное и максимальное десятичные числа с типом данных SQL на источнике данных.  
  
 Значения, возвращаемые этими функциями для столбца или параметра size соответствует «точность» как определено в ODBC 2. *x*. Тем не менее значения не обязательно соответствуют значениям, возвращаемым в SQL_DESC_PRECISION или других одно поле дескриптора. То же самое верно для десятичных цифр, которые соответствуют «scale» как определено в ODBC 2. *x*. Не обязательно соответствуют значениям, возвращаемым в SQL_DESC_SCALE или других одного поля дескриптора, но поступают из разных дескриптора поля в зависимости от типа данных. Дополнительные сведения см. в разделе [размер столбца](../../../odbc/reference/appendixes/column-size.md) и [десятичные цифры](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Аналогичным образом значения для передачи октет длина поставляются из SQL_DESC_LENGTH. Они извлекаются из SQL_DESC_OCTET_LENGTH поля дескриптора для всех символьных и двоичных типов. Нет поля дескриптора, содержащий эти сведения для других типов.  
  
 Значение в поле одного дескриптора, столбцов SQL_DESC_DISPLAY_SIZE соответствует значение размера отображения для всех типов данных.  
  
 Поля дескрипторов описывают характеристики результирующего набора. Поля дескриптора не содержат допустимых значений данных перед выполнением инструкции. Значения для столбца размера, десятичные цифры и отображения размер, возвращенный **SQLColumns**, **SQLProcedureColumns**, и **SQLGetTypeInfo**, с другой стороны, возврат характеристики объектов базы данных, таких как столбцы таблицы и типов данных, которые существуют в источнике данных каталога. Аналогичным образом в ее результирующий набор **SQLColAttribute** возвращает размер столбца, десятичные цифры и передача октет длина столбцов в источнике данных; эти значения не обязательно совпадают со значениями в SQL_DESC_PRECISION SQL_ DESC_SCALE и SQL_DESC_OCTET_LENGTH поля дескриптора.  
  
 Дополнительные сведения об этих полях дескриптора см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 См. также:  
  
-   [Размер столбца](../../../odbc/reference/appendixes/column-size.md)  
-   [Десятичные цифры](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Длина в октетах передачи](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Размер экрана](../../../odbc/reference/appendixes/display-size.md)

