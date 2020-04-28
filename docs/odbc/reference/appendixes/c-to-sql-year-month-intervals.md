---
title: 'C в SQL: интервалы за год-месяц | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ec7bfda0015883c8470dd453c7ae5de9bfd6cec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306615"
---
# <a name="c-to-sql-year-month-intervals"></a>Преобразование из C в SQL: интервалы месяцев года
Идентификаторы для следующих типов данных ODBC C для интервала года:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы данные из интервала в месяц. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Длина байта столбца >= Длина байтового символа<br /><br /> Длина байта столбца < длина байтовой кодировки [a]<br /><br /> Значение данных не является допустимым литералом интервала|Недоступно<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Длина символа столбца >= символьная длина данных<br /><br /> Длина символов в столбцах < символьной длины данных [a]<br /><br /> Значение данных не является допустимым литералом интервала|Недоступно<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Преобразование интервала с одним полем не привело к усечению целых цифр<br /><br /> Преобразование привело к усечению целых цифр|Недоступно<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Значение данных было преобразовано без усечения каких бы то ни было полей<br /><br /> Одно или несколько полей значения данных были усечены во время преобразования|Недоступно<br /><br /> 22015|  
  
 [a] все типы данных интервала C могут быть преобразованы в символьный тип данных.  
  
 [b] Если поле типа в структуре интервала имеет значение, равное одному полю (SQL_YEAR или SQL_MONTH), то тип времени C можно преобразовать в любой точный числовой (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL или SQL_NUMERIC).  
  
 По умолчанию при преобразовании типа «интервал C» к соответствующему типу SQL «год-месяц».  
  
 Драйвер не учитывает значение длины или индикатора при преобразовании данных из типа данных Interval C и предполагает, что размер буфера данных равен размеру типа данных Interval C. Значение length/индикатора передается в аргументе *StrLen_Or_Ind* в **SQLPutData** и в буфере, указанном аргументом *StrLen_or_IndPtr* в **SQLBindParameter**. Буфер данных указывается с помощью аргумента *датаптр* в **SQLPutData** и аргумента *параметервалуептр* в **SQLBindParameter**.
