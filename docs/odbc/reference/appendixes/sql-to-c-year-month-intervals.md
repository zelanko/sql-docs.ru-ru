---
title: "SQL, чтобы интервалы год месяц C: | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4acd46374597b19849abfaa7cb547c8b6af23bd9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sql-to-c-year-month-intervals"></a>SQL, чтобы интервалы год месяц C:
Идентификаторы типа данных ODBC SQL interval год месяц следующие:  
  
 SQL_INTERVAL_YEAR  
  
 SQL_INTERVAL_MONTH  
  
 SQL_INTERVAL_YEAR_TO_MONTH  
  
 Следующая таблица показывает ODBC C типы данных, к какой год месяц интервала данных SQL могут быть преобразованы. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH []<br /><br /> SQL_C_INTERVAL_YEAR []<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH []|Часть поля не усекаются замыкающие<br /><br /> В конце поля часть усечена<br /><br /> Начальные точность целевого объекта недостаточно велик для хранения данных из источника|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b]<br /><br /> SQL_C_UTINYINT [b]<br /><br /> SQL_C_USHORT [b]<br /><br /> SQL_C_SHORT [b]<br /><br /> SQL_C_SLONG [b]<br /><br /> SQL_C_ULONG [b]<br /><br /> SQL_C_NUMERIC [b]<br /><br /> SQL_C_BIGINT [b]|Интервал точность была одним полем и преобразован без усечения данных<br /><br /> Интервал точность была отдельное поле и усеченное всего<br /><br /> Точность интервала не был одного поля|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных в байтах<br /><br /> Размер типа данных C|н/д<br /><br /> 22003<br /><br /> 22015|  
_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Байтовая длина данных > *BufferLength*|data<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_CHAR|Длина байтов символьной < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) > = *BufferLength*|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина символьной < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) > = *BufferLength*|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
  
 [] типа год месяц интервалом типа SQL можно преобразовать в любой тип C интервал месяца года.  
  
 [b] Если точности интервала одно поле (один год или месяц), можно преобразовать интервал тип SQL для любой точное числовое значение (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  
  
 Преобразования по умолчанию интервала тип SQL — соответствующие типы данных C интервал. Затем приложение привязывает столбца или параметра (или задает поле SQL_DESC_DATA_PTR в соответствующей записи Отменить) для указания инициализированный SQL_INTERVAL_STRUCT структуры (или передает указатель в качестве структуруSQL_INTERVAL_STRUCT*TargetValuePtr* аргумента в вызове **SQLGetData**).
