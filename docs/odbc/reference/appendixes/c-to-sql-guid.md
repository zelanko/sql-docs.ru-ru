---
title: 'От от C до СЗЛ: GUID Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3b559499273e885e23da10d9093a0ce9ff92393
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306625"
---
# <a name="c-to-sql-guid"></a>Преобразование из C в SQL: GUID
Идентификатор для типа данных GUID ODBC C:  
  
 SQL_C_GUID  
  
 В следующей таблице показаны типы данных ODBC S'L, в которые могут быть преобразованы данные GUID C. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Длина столбца байт >No 36|Недоступно|  
|SQL_VARCHAR|Длина столбца байт < 36|22001|  
|SQL_LONGVARCHAR|Значение данных не является действительным GUID|22018|  
|SQL_WCHAR|Длина символа столбца >36|Недоступно|  
|SQL_WVARCHAR|Длина символа столбца < 36|22001|  
|SQL_WLONGVARCHAR|Значение данных не является действительным GUID|22018|  
|SQL_GUID|Нет|Недоступно|  
  
 Все гексидекемальные значения действительны как GUID.  
  
 Драйвер игнорирует значение длины/индикатора при преобразовании данных из типа данных GUID C и предполагает, что размер буфера данных является размером типа данных GUID C. Значение длины/индикатора передается в *StrLen_or_Ind* аргументе в **S'LPutData** и в буфере, указанном с *аргументом StrLen_or_IndPtr* в **S'LBindParameter**. Буфер данных указан с аргументом *DataPtr* в **S'LPutData** и аргументом *ParameterValuePtr* в **S'LBindParameter**.
