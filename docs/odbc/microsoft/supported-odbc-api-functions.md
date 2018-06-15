---
title: Поддерживаемые функции ODBC API | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC, API functions
- ODBC SQL grammar, API functions mapped to driver (table) [ODBC]
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5d7044cb0a4e963fdea39852593112c33fa8908
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913339"
---
# <a name="supported-odbc-api-functions"></a>Поддерживаемые ODBC функций API
Выравнивание предназначено для уведомления приложения, какие функции доступны на него с помощью драйвера. Microsoft Desktop базы данных драйверы ODBC поддерживают все функции основных компонентов и уровня 1.  
  
 Дополнительные сведения об уровнях совместимости для функций и грамматики см. в разделе [уровни соответствия](../../odbc/reference/develop-app/conformance-levels.md) в *справочнике программиста ODBC*.  
  
 Поддержка функций ODBC API может зависеть от драйвера, используемого. В следующей таблице перечислены поддержка функций. Крайний слева столбец содержит ссылку на страницу общие справочные сведения для каждой функции. Эти ссылки страницы перечислены в алфавитном порядке [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md) в области [справочнике программиста ODBC](../../odbc/reference/odbc-programmer-s-reference.md). Столбцы для правого укажите ссылки на относящиеся к драйверу примечания о каждой функции, поддерживаемые. Эти разделы драйвера перечислены в разделе «Другие программирования подробности» для каждого драйвера. Кроме того Если же примечания о функции применяются все системной базы данных драйверы ODBC, крайний правый столбец содержит ссылку на раздел, где приведены сведения о поддержке драйверов базы данных рабочего стола для этой функции. Эти разделы перечислены в конце текущего раздела («поддерживается функций ODBC API»).  
  
|Функция ODBC|Заметки о драйвера доступа|заметки о dBASE драйвера|Заметки о драйвера Paradox|Текст заметки файл драйвера|Заметки о драйвера Excel|Заметки, относящиеся к все драйверы|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Доступ](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Доступ](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[Доступ](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[dBASE](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[Доступ](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[dBASE](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[Доступ](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)||  
GetStmtOption] (.. / Topic/SQLGetStmtOption%20Function.md)|[Все драйверы](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)||||||  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[Доступ](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)||||||[Доступ](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)|  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[Доступ](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[dBASE](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Все драйверы](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[Доступ](../../odbc/microsoft/sqlstatistics-access-driver.md)|[dBASE](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[Доступ](../../odbc/microsoft/sqltables-access-driver.md)|[dBASE](../../odbc/microsoft/sqltables-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltables-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)||  
Transact] (.. / Topic/SQLTransact%20Function.md)|[Доступ](../../odbc/microsoft/sqltransact-access-driver.md)|[dBASE](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Текстовый файл](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 В следующих разделах приводятся замечания о функции ODBC. Следующие примечания относятся к всех драйверов базы данных ODBC.  
  
-   [SQLGetData (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [SQLGetStmtOption (драйверы для настольных баз данных)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (драйверы для баз данных на настольном компьютере)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
