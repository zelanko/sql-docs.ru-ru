---
title: "C в SQL: год месяц интервалы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 880564e5883299b5f79df4f0480ab81ae8c9de1c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-year-month-intervals"></a>C в SQL: интервалом месяц года
Идентификаторы для типов данных ODBC C интервал месяца года следующие:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 В следующей таблице показаны ODBC SQL типы данных, к какой год месяц C интервал данные могут преобразовываться. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR []<br /><br /> SQL_VARCHAR []<br /><br /> SQL_LONGVARCHAR []|Длина столбца в байтах > = байт символов<br /><br /> Длина в байтах столбца < символов длина byte []<br /><br /> Значение данных не допустимый интервал литерала|н/д<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR []<br /><br /> SQL_WVARCHAR []<br /><br /> SQL_WLONGVARCHAR []|Длина столбца символ > = длина символов в данных<br /><br /> Длина столбца символ < длина данных []<br /><br /> Значение данных не допустимый интервал литерала|н/д<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Преобразование интервала одному полю не привел к усечение всего цифр<br /><br /> Преобразование привело к усечению всей цифр|н/д<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Преобразовать значение данных было без усечения всех полей<br /><br /> Одно или несколько полей значений данных были усечены во время преобразования|н/д<br /><br /> 22015|  
  
 [] типы данных всех C интервал можно преобразовать в символьный тип данных.  
  
 [b] Если поле "тип" в структуре интервал таким образом, что интервал состоит из одного поля (SQL_YEAR или SQL_MONTH), тип интервала C можно преобразовать в любой точное числовое значение (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL или SQL_NUMERIC).  
  
 Преобразование типа C интервал по умолчанию — соответствующий тип SQL интервал месяца года.  
  
 Драйвер не учитывает значение длины/индикатора при преобразовании данных из типа данных C интервал и предполагает, что размер буфера данных размер типа данных C интервал. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.
