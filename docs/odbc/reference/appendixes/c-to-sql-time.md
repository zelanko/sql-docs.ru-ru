---
title: 'От от C до СЗЛ: Время Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 264ce7751072b79163923f0c141542680f7b02bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304767"
---
# <a name="c-to-sql-time"></a>Преобразование из C в SQL: время
Идентификатор для типа данных ODBC C:  
  
 SQL_C_TYPE_TIME  
  
 В следующей таблице показаны типы данных ODBC S'L, к которым могут быть преобразованы данные C. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца байт >No 8<br /><br /> Длина столбца байт < 8<br /><br /> Значение данных не является действительным временем|Недоступно<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символа столбца >No 8<br /><br /> Длина символа колонны < 8<br /><br /> Значение данных не является действительным временем|Недоступно<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Значение данных является действительным временем<br /><br /> Значение данных не является действительным временем|Недоступно<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Значение данных является действительным временем<br /><br /> Значение данных не является действительным временем|Недоступно<br /><br /> 22007|  
  
 Часть даты метки времени устанавливается к текущей дате, а фракционная секундная часть метки времени установлена до нуля.  
  
 Для получения информации о том, какие [C Data Types](../../../odbc/reference/appendixes/c-data-types.md)значения действительны в структуре SQL_C_TYPE_TIME, см.  
  
 Когда данные c время преобразуются в данные о символах S'L, полученные данные о символах в формате «*hh*:*mm*:*ss».*  
  
 Драйвер игнорирует значение длины/индикатора при преобразовании данных из типа данных времени C и предполагает, что размер буфера данных — это размер типа данных C. Значение длины/индикатора передается в *StrLen_or_Ind* аргументе в **S'LPutData** и в буфере, указанном с *аргументом StrLen_or_IndPtr* в **S'LBindParameter**. Буфер данных указан с аргументом *DataPtr* в **S'LPutData** и аргументом *ParameterValuePtr* в **S'LBindParameter**.
