---
title: 'SQL в C: Интервалы месяцев года | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c7412226dd0674022da022b0a0a63e5bf2063cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065042"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL в C: Интервалы месяцев года

Ниже перечислены идентификаторы для интервальных типов данных ODBC SQL год месяц.

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

Следующая таблица показывает ODBC C типы данных, в какие год месяц может преобразовать интервал данных SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Идентификатор типа C|Тест|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH[a]<br /><br /> SQL_C_INTERVAL_YEAR [a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH[a]|В конце часть полей не усечены<br /><br /> В конце поля часть усечена<br /><br /> Точность целевого объекта недостаточно велик для хранения данных из источника|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b]<br /><br /> SQL_C_UTINYINT [b]<br /><br /> SQL_C_USHORT [b]<br /><br /> SQL_C_SHORT [b]<br /><br /> SQL_C_SLONG [b]<br /><br /> SQL_C_ULONG [b]<br /><br /> SQL_C_NUMERIC[b]<br /><br /> SQL_C_BIGINT [b]|Интервал точности был одним полем и данные преобразованы без усечения<br /><br /> Интервал точности был один поле и усеченное совершенно<br /><br /> Точность интервала не был одним полем|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных в байтах<br /><br /> Размер типа данных C|Н/Д<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Data<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
|SQL_C_CHAR|Длина байтов символьной < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) > = *BufferLength*|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина символьной < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) > = *BufferLength*|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
  
 [] типа год месяц интервале тип SQL можно преобразовать в любой тип интервала C год месяц.  
  
 [b] Если точности интервала одно поле (один год или месяц), интервал тип SQL можно преобразовать в любой точный числовой (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  

## <a name="default-conversions"></a>Преобразования по умолчанию

Преобразования по умолчанию интервала тип SQL — соответствующие типы данных C интервал. Затем приложение выполняет привязку столбца или параметра (или задает поле SQL_DESC_DATA_PTR в соответствующую запись Отменить) для на инициализированный SQL_INTERVAL_STRUCT структуру (или передает указатель на структуру SQL_ INTERVAL_STRUCT как *TargetValuePtr* аргумента в вызове **SQLGetData**).
