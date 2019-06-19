---
title: 'C в SQL: Интервалы месяцев года | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d12727f9298eb63fe10b44c48b9d3b7996a839d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159287"
---
# <a name="c-to-sql-year-month-intervals"></a>C в SQL: Интервалы месяцев года
Идентификаторы для интервальных типов данных ODBC C год месяц следующие:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 Следующая таблица показывает ODBC SQL типы данных, к какой год месяц интервал C данные могут преобразовываться. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR, [a]<br /><br /> SQL_LONGVARCHAR [a]|Длина столбца в байтах > = байтов символов<br /><br /> Длина в байтах столбца < символов байт []<br /><br /> Значение данных не является допустимое значение литерала интервала|н/д<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Длина столбца символ > = символьную длину данных<br /><br /> Длина столбца символ < символ длину данных, [a]<br /><br /> Значение данных не является допустимое значение литерала интервала|н/д<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Преобразование интервала одному полю не привел к усечение целой части<br /><br /> Преобразование привело к усечению целой части|н/д<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Значение данных был преобразован без усечения всех полей<br /><br /> Одно или несколько полей данных значения были усечены во время преобразования|н/д<br /><br /> 22015|  
  
 [a] все C интервальных типов данных могут преобразовываться в символьный тип данных.  
  
 [b] тип является ли поле в структуре интервал таким образом, интервал — это единственное поле (SQL_YEAR или SQL_MONTH), тип интервала C могут преобразовываться в любой точный числовой (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL или SQL_NUMERIC).  
  
 Преобразования по умолчанию интервала тип C — интервала год месяц в соответствующий тип SQL.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных из типа данных интервала C и предполагает, что размер буфера данных размер типа данных interval C. Значение длины и индикатора, переданное в *StrLen_or_Ind* аргумента в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумента в **SQLBindParameter**. Буфер данных указывается с помощью *DataPtr* аргумента в **SQLPutData** и *ParameterValuePtr* аргумента в **SQLBindParameter**.
