---
description: 'Преобразование из C в SQL: числовые данные'
title: 'C в SQL: numeric | Документация Майкрософт'
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
ms.openlocfilehash: 111d2bedf6b988255a569587fd766406b6b4176a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421518"
---
# <a name="c-to-sql-numeric"></a>Преобразование из C в SQL: числовые данные
Для числовых типов данных ODBC C используются следующие идентификаторы:  
  
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
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы числовые данные C. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Число цифр <= длина столбца в байтах<br /><br /> Число цифр > длина столбца в байтах|Недоступно<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Число символов <= длина символа столбца<br /><br /> Число символов > длина символа столбца|Недоступно<br /><br /> 22001|  
|SQL_DECIMAL [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]|Данные, преобразованные без усечения или с усеченными дробными цифрами<br /><br /> Данные, преобразованные с усечением целых цифр|Недоступно<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Данные находятся в диапазоне типа данных, в который преобразуется число<br /><br /> Данные выходят за пределы диапазона типа данных, в который преобразуется число|Недоступно<br /><br /> 22003|  
|SQL_BIT|Данные равны 0 или 1<br /><br /> Данные больше 0, меньше 2 и не равны 1<br /><br /> Данные меньше 0 или больше или равны 2|Недоступно<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR [a]<br /><br /> SQL_INTERVAL_MONTH [a]<br /><br /> SQL_INTERVAL_DAY [a]<br /><br /> SQL_INTERVAL_HOUR [a]<br /><br /> SQL_INTERVAL_MINUTE [a]<br /><br /> SQL_INTERVAL_SECOND [a]|Данные не усечены.<br /><br /> Данные усечены.|Недоступно<br /><br /> 22015|  
  
 [a] эти преобразования поддерживаются только для точных числовых типов данных (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC). Они не поддерживаются для приблизительных числовых типов данных (SQL_C_FLOAT или SQL_C_DOUBLE). Типы данных с точным числовым значением в C не могут быть преобразованы в тип SQL Interval, для которого точность не является одним полем.  
  
 [b] для варианта "н/д" драйвер может дополнительно возвращать SQL_SUCCESS_WITH_INFO и 01S07, если имеется дробное усечение.  
  
 Драйвер игнорирует значение длины или индикатора при преобразовании данных из числовых типов данных C и предполагает, что размер буфера данных равен размеру числового типа данных C. Значение length/индикатора передается в аргументе *StrLen_Or_Ind* в **SQLPutData** и в буфере, указанном аргументом *StrLen_or_IndPtr* в **SQLBindParameter**. Буфер данных указывается с помощью аргумента *датаптр* в **SQLPutData** и аргумента *параметервалуептр* в **SQLBindParameter**.
