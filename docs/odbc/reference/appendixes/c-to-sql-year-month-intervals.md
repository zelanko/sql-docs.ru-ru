---
title: 'От от C до СЗЛ: Интервалы с года миадой (ru) Документы Майкрософт'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306615"
---
# <a name="c-to-sql-year-month-intervals"></a>Преобразование из C в SQL: интервалы месяцев года
Идентификаторы для годового интервала ODBC C типов данных являются:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 В следующей таблице показаны типы данных ODBC S'L, к которым могут быть преобразованы данные интервала C за год. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца byte >- длина персонажа байт<br /><br /> Длина байта колонки < длина персонажа байта<br /><br /> Значение данных не является допустимой интервалом буквального|Недоступно<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символа столбца >- длина символов данных<br /><br /> Длина символа столбца < длина символов данных<br /><br /> Значение данных не является допустимой интервалом буквального|Недоступно<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_NUMERIC<br /><br /> SQL_DECIMAL|Преобразование интервала с одним полем не привело к усечению целых цифр<br /><br /> Преобразование привело к усечению целых цифр|Недоступно<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Значение данных преобразовалось без усечения любых полей<br /><br /> Одно или несколько полей значения данных были усечены во время преобразования|Недоступно<br /><br /> 22015|  
  
 Все типы интервальных данных C могут быть преобразованы в тип данных символов.  
  
 Если поле типа в интерводной структуре таково, что интервал представляет собой одно поле (SQL_YEAR или SQL_MONTH), тип интервала C может быть преобразован в любой точный число (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL или SQL_NUMERIC).  
  
 Преобразование по умолчанию типа интервала C происходит к соответствующему годовому периоду S'L.  
  
 Драйвер игнорирует значение длины/индикатора при преобразовании данных из типа данных интервала C и предполагает, что размер буфера данных представляет собой размер типа данных интервала C. Значение длины/индикатора передается в *StrLen_or_Ind* аргументе в **S'LPutData** и в буфере, указанном с *аргументом StrLen_or_IndPtr* в **S'LBindParameter**. Буфер данных указан с аргументом *DataPtr* в **S'LPutData** и аргументом *ParameterValuePtr* в **S'LBindParameter**.
