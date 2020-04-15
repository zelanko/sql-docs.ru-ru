---
title: 'От к СЗЛ: Число (ч. 4) Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbc0a994ef95f2deca29c8a4cbb06f3167b0433f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304735"
---
# <a name="c-to-sql-numeric"></a>Преобразование из C в SQL: числовые данные
Идентификаторы для численных типов данных ODBC C:  
  
 SQL_C_STINYINT  
  
 SQL_C_SLONG  
  
 SQL_C_UTINYINT  
  
 SQL_C_ULONG  
  
 SQL_C_TINYINT  
  
 SQL_C_LONG  
  
 SQL_C_SSHORT  
  
 SQL_C_FLOAT  
  
 SQL_C_USHORT  
  
 SQL_C_DOUBLE  
  
 SQL_C_SHORT  
  
 SQL_C_NUMERIC  
  
 SQL_C_SBIGINT  
  
 SQL_C_UBIGINT  
  
 В следующей таблице показаны типы данных ODBC S'L, в которые могут быть преобразованы числовые данные C. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Количество цифр <и длина столбца байт<br /><br /> Количество цифр > длина столбца byte|Недоступно<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Количество символов <- длина символа столбца<br /><br /> Количество символов > длина символов колонки|Недоступно<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT|Данные преобразуются без усечения или с усеченными дробными цифрами<br /><br /> Данные, преобразованные с усеиванием целых цифр|Недоступно<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Данные находятся в пределах типа данных, в который преобразуется число<br /><br /> Данные не входят в диапазон типа данных, в который преобразуется|Недоступно<br /><br /> 22003|  
|SQL_BIT|Данные 0 или 1<br /><br /> Данные превышают 0, менее 2 и не равны 1<br /><br /> Данные меньше, чем 0 или больше, чем или равны 2|Недоступно<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND|Данные не усечены.<br /><br /> Данные усечены.|Недоступно<br /><br /> 22015|  
  
 Эти преобразования поддерживаются только для точных типов численных данных (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC). Они не поддерживаются для приблизительных типов численных данных (SQL_C_FLOAT или SQL_C_DOUBLE). Точные типы численных C данных не могут быть преобразованы в интервал типа S'L, точность интервала которого не является одним полем.  
  
 В случае "n/a" водитель может по желанию вернуть SQL_SUCCESS_WITH_INFO и 01S07 при дробном усечении.  
  
 Драйвер игнорирует значение длины/индикатора при преобразовании данных из типов данных числового C и предполагает, что размер буфера данных является размером типа данных числа C. Значение длины/индикатора передается в *StrLen_or_Ind* аргументе в **S'LPutData** и в буфере, указанном с *аргументом StrLen_or_IndPtr* в **S'LBindParameter**. Буфер данных указан с аргументом *DataPtr* в **S'LPutData** и аргументом *ParameterValuePtr* в **S'LBindParameter**.
