---
title: 'От от C до СЗЛ: Дата Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa3df8aaee03472076b3241cb9bb60e2a307e28b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298852"
---
# <a name="c-to-sql-date"></a>Преобразование из C в SQL: даты
Идентификатор для типа данных ODBC C:  
  
 SQL_C_TYPE_DATE  
  
 В следующей таблице показаны типы данных ODBC S'L, к которым могут быть преобразованы данные C на дату. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца байт >No 10<br /><br /> Длина столбца байт < 10<br /><br /> Значение данных не является действительной датой|Недоступно<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символа столбца >10 евро<br /><br /> Длина символа столбца < 10<br /><br /> Значение данных не является действительной датой|Недоступно<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Значение данных является действительной датой<br /><br /> Значение данных не является действительной датой|Недоступно<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Значение данных является действительной датой.<br /><br /> Значение данных не является действительной датой|Недоступно<br /><br /> 22007|  
  
 Время, отведенное от метки времени, сведено к нулю.  
  
 Для получения информации о том, какие [C Data Types](../../../odbc/reference/appendixes/c-data-types.md)значения действительны в структуре SQL_C_TYPE_DATE, см.  
  
 Когда данные даты C преобразуются в данные о символах S'L, полученные данные о символах в формате *«yyyy*-*mm*-*dd».*  
  
 Драйвер игнорирует значение длины/индикатора при преобразовании данных из типа данных даты C и предполагает, что размер буфера данных представляет собой размер типа данных C. Значение длины/индикатора передается в *StrLen_or_Ind* аргументе в **S'LPutData** и в буфере, указанном с *аргументом StrLen_or_IndPtr* в **S'LBindParameter**. Буфер данных указан с аргументом *DataPtr* в **S'LPutData** и аргументом *ParameterValuePtr* в **S'LBindParameter**.
