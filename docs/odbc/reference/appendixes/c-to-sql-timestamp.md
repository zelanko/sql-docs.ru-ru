---
title: "От от c до S'L: Меткая метка времени Документы Майкрософт"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3102e5043527a1aa9463980c9dd546839cb92f37
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283754"
---
# <a name="c-to-sql-timestamp"></a>Преобразование из C в SQL: отметки времени
Идентификатор для типа данных timestamp ODBC C:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 В следующей таблице показаны типы данных ODBC S'L, в которые могут быть преобразованы данные временной метки C. Для объяснения столбцов и терминов в [Converting Data from C to SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)таблице см.  
  
|Идентификатор типа S'L|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца byte >- длина персонажа байт<br /><br /> 19 <- длина длины байт-< символа byte<br /><br /> Длина столбца байт < 19<br /><br /> Значение данных не является допустимой меткой времени|Недоступно<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символа столбца >- длина символов данных<br /><br /> 19 <- длина символа столбца < длина символов данных<br /><br /> Длина символа колонны < 19<br /><br /> Значение данных не является допустимой меткой времени|Недоступно<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Поля времени равны нулю<br /><br /> Поля времени ненулевые<br /><br /> Значение данных не содержит допустимую дату|Недоступно<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Фракционные секундные поля равны нулю<br /><br /> Фракционные секундные поля незеролевые<br /><br /> Значение данных не содержит допустимого времени|Недоступно<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Фракционные секундные поля не усечены<br /><br /> Фракционные секундные поля усечены<br /><br /> Значение данных не является допустимой меткой времени|Недоступно<br /><br /> 22008<br /><br /> 22007|  
  
 Поля даты структуры метки времени игнорируются.  
  
 Для получения информации о том, какие [C Data Types](../../../odbc/reference/appendixes/c-data-types.md)значения действительны в структуре SQL_C_TIMESTAMP, см.  
  
 При преобразовании данных timestamp C в данные о символах S'L, полученные данные о символах понижались в "*yyyy*-*mm*-*dd* *hh:**mm*:*ss ss.** f...* Формат.  
  
 Драйвер игнорирует значение длины/индикатора при преобразовании данных из типа данных timestamp C и предполагает, что размер буфера данных представляет собой размер типа данных Timestamp C. Значение длины/индикатора передается в *StrLen_or_Ind* аргументе в **S'LPutData** и в буфере, указанном с *аргументом StrLen_or_IndPtr* в **S'LBindParameter**. Буфер данных указан с аргументом *DataPtr* в **S'LPutData** и аргументом *ParameterValuePtr* в **S'LBindParameter**.
