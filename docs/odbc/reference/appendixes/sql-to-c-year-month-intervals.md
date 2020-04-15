---
title: 'СЗЛ в C: Интервалы с годами (ru) Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba79a4d6165a43676634a6b79db56b88f5bcc234
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296394"
---
# <a name="sql-to-c-year-month-intervals"></a>Преобразование данных из SQL в C: интервалы месяцев года

Идентификаторы для типов данных ODBC S'L в течение года:

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные интервала года. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  

|Идентификатор типа C|Тест|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH<br /><br /> SQL_C_INTERVAL_YEAR<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH|Трейлинговые поля часть не усечены<br /><br /> Трейлинговые поля часть усеченных<br /><br /> Ведущая точность мишени недостаточно велика для хранения данных из источника|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_NUMERIC<br /><br /> SQL_C_BIGINT|Интервал точность была одно поле и данные были преобразованы без усечения<br /><br /> Интервал точность была одним полем и усеченных целом<br /><br /> Интервал точность не было ни одного поля|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных в байтах<br /><br /> Размер типа данных C|Недоступно<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_CHAR|Длина байта персонажа < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр >*BufferLength*|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина персонажа < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр >*BufferLength*|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
  
 Тип интервала СЗЛ в течение года может быть преобразован в любой тип интервала C за год.  
  
 Если точность интервала представляет собой одно поле (одно из YEAR или MONTH), то тип интервала S'L может быть преобразован в любой точный число (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  

## <a name="default-conversions"></a>Преобразования по умолчанию

Преобразование по умолчанию интервала типа S'L происходит в соответствующий тип данных интервала C. Затем приложение связывает столбец или параметр (или устанавливает поле SQL_DESC_DATA_PTR в соответствующей записи ARD), чтобы указать на инициализированную структуру SQL_INTERVAL_STRUCT (или передает указатель на SQL_ INTERVAL_STRUCT структуру в качестве аргумента *TargetValuePtr* в вызове к **S'LGetData).**
