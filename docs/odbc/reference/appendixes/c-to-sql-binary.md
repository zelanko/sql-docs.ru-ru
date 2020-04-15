---
title: 'От до СЗЛ: Двоичный Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binary data type [ODBC]
- data conversions from C to SQL types [ODBC], binary
- binary data transfers [ODBC]
- converting data from c to SQL types [ODBC], binary
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 818de0086ce3996cc1f6194311d2a2bb80c9f564
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292120"
---
# <a name="c-to-sql-binary"></a>Преобразование из C в SQL: двоичные данные
Идентификатор для двоичного типа данных ODBC C:  
  
 SQL_C_BINARY  
  
 В следующей таблице показаны типы данных ODBC S'L, в которые могут быть преобразованы двоичные данные C. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина байт данных <и длина столбца байт<br /><br /> Длина байт данных > длина столбца byte|Недоступно<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символов данных <- длина символа столбца<br /><br /> Длина символов данных > длина символов колонки|Недоступно<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|Длина данных байта - длина данных S'L<br /><br /> Длина данных байта <> длина данных S'L|Недоступно<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|Длина данных <и длина столбца<br /><br /> Длина данных > длина столбца|Недоступно<br /><br /> 22001|
