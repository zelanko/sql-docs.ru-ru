---
description: 'Преобразование из C в SQL: двоичные данные'
title: 'C в SQL: binary | Документация Майкрософт'
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
ms.openlocfilehash: 87e6d6a58afb41f03027fbfd25aaca50af5e7bd3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500047"
---
# <a name="c-to-sql-binary"></a>Преобразование из C в SQL: двоичные данные
Идентификатор двоичного типа данных ODBC C:  
  
 SQL_C_BINARY  
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы двоичные данные C. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина байтового <данных = длина столбца в байтах<br /><br /> Длина байта данных > столбца длиной в байтах|Недоступно<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Символьная длина <данных = длина символа столбца<br /><br /> Длина символьной длины данных > столбцах|Недоступно<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|Длина данных в байтах = длина данных SQL<br /><br /> Длина данных в байтах <> длина данных SQL|Недоступно<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|Длина <данных = длина столбца<br /><br /> Длина данных > длина столбца|Недоступно<br /><br /> 22001|
