---
title: Поддерживаемые функции API ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC, API functions
- ODBC SQL grammar, API functions mapped to driver (table) [ODBC]
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec6ceaf57d8fe3c5325f85a9644cf4c8016663e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304105"
---
# <a name="supported-odbc-api-functions"></a>Поддерживаемые функции API ODBC
Цель выравнивания заключается в том, чтобы сообщить приложению, какие функции доступны ему от водителя. Драйверы настольной базы данных Microsoft ODBC поддерживают все функции Core и Level 1.  
  
 Для получения дополнительной информации об уровнях соответствия для *ODBC Programmer's Reference*функций и грамматики, [см.](../../odbc/reference/develop-app/conformance-levels.md)  
  
 Поддержка функций ODBC API может зависеть от используемого драйвера. В следующей таблице кратко излагается поддержка функций. В левой колонке содержится ссылка на общую справочную страницу для каждой функции. Эти справочные страницы перечислены в алфавитном порядке в разделе [справки ODBC API,](../../odbc/reference/syntax/odbc-api-reference.md) в разделе [ODBC программиста](../../odbc/reference/odbc-programmer-s-reference.md). Столбцы справа предоставляют ссылки на заметки, связанные с драйвером, о каждой поддерживаемой функции. Эти темы, посвященные конкретным драйверам, перечислены в разделе "Другие детали программирования" для каждого драйвера. Кроме того, если одни и те же замечания о функции относятся ко всем драйверам настольных баз данных ODBC, то самая правая колонка предоставляет ссылку на тему, которая обобщает поддержку драйверов настольных баз данных для этой функции. Эти темы перечислены в конце текущего раздела ("Поддерживаемые функции API ODBC").  
  
|Функция ODBC|Заметки о драйверах доступа|dBASE Драйвер конкретных заметок|Парадокс Драйвер конкретных отмечает|Заметки драйвера для текста|Заметки, связанные с драйвером Excel|Заметки, имеющие отношение ко всем водителям|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[СЗЛКолАтрибуты](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Доступ](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Доступ](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[Доступ](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[Dbase](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[Доступ](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[Dbase](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[Доступ](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[СЗЛГетСтмтOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[Доступ](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[Доступ](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[СЗЛЕтКоннектОпция](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[Доступ](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[Dbase](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[СЗЛСетКурсОрНамейм](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[функция SQLSetPos;](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[СЗЛСЕтПрокрутисОпции](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[СЗЛСетСтмтOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[Доступ](../../odbc/microsoft/sqlstatistics-access-driver.md)|[Dbase](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[Доступ](../../odbc/microsoft/sqltables-access-driver.md)|[Dbase](../../odbc/microsoft/sqltables-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqltables-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[СЗЛТрансакт](../../odbc/reference/syntax/sqltransact-function.md)|[Доступ](../../odbc/microsoft/sqltransact-access-driver.md)|[Dbase](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Парадокс](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 Ниже приведены замечания по поводу функций ODBC. Эти замечания распространяются на всех драйверов настольных баз данных ODBC.  
  
-   [SQLGetData (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [Драйверы базы данных для настольных компьютеров S'LGetStmtOption (драйверы базы данных)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
