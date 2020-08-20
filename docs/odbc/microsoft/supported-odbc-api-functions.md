---
description: Поддерживаемые функции API ODBC
title: Поддерживаемые функции API ODBC | Документация Майкрософт
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
ms.openlocfilehash: 61dca7de4a9a532789a2b448fad812ae3daf76ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500097"
---
# <a name="supported-odbc-api-functions"></a>Поддерживаемые функции API ODBC
Целью выравнивания является информирование приложения о том, какие функции доступны из драйвера. Драйверы базы данных Microsoft ODBC для настольных систем поддерживают все функции ядра и уровня 1.  
  
 Дополнительные сведения о уровнях соответствия для функций и грамматики см. в разделе [уровни соответствия](../../odbc/reference/develop-app/conformance-levels.md) в *справочнике программиста ODBC*.  
  
 Поддержка функций API ODBC может зависеть от используемого драйвера. В следующей таблице приведена сводка по поддержке функций. В крайнем левом столбце содержится ссылка на общую страницу ссылки для каждой функции. Эти справочные страницы перечислены в алфавитном порядке в разделе [Справочник по ODBC API](../../odbc/reference/syntax/odbc-api-reference.md) в разделе [Справочник программиста по ODBC](../../odbc/reference/odbc-programmer-s-reference.md). В столбцах справа содержатся ссылки на заметки, относящиеся к драйверу, о каждой поддерживаемой функции. Эти разделы, относящиеся к драйверам, перечислены в разделе "другие сведения о программировании" для каждого драйвера. Кроме того, если одни и те же замечания о функции применяются ко всем драйверам базы данных ODBC для настольных систем, в крайнем правом столбце содержится ссылка на раздел, в котором приведена сводка по поддержке драйверов баз данных настольных систем. Эти разделы перечислены в конце текущего раздела ("Поддерживаемые функции API ODBC").  
  
|Функция ODBC|Доступ к заметкам, относящимся к драйверу|замечания, относящиеся к драйверу dBASE|Заметки, относящиеся к драйверу Paradox|Примечания для текстовых файлов, относящиеся к драйверу|Заметки, относящиеся к драйверу Excel|Примечания, относящиеся ко всем драйверам|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Доступ](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Доступ](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[Доступ](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[dBASE](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[Доступ](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[dBASE](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[Доступ](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[Доступ](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[Доступ](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[Доступ](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[dBASE](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[функция SQLSetPos;](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[Доступ](../../odbc/microsoft/sqlstatistics-access-driver.md)|[dBASE](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[Доступ](../../odbc/microsoft/sqltables-access-driver.md)|[dBASE](../../odbc/microsoft/sqltables-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqltables-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)|[Доступ](../../odbc/microsoft/sqltransact-access-driver.md)|[dBASE](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Таблица](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 В следующих разделах содержатся примечания о функциях ODBC. Эти замечания относятся ко всем драйверам базы данных ODBC для настольных систем.  
  
-   [SQLGetData (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [SQLGetStmtOption (драйверы базы данных для настольных систем)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
