---
title: Функции ODBC и визуальный драйвер FoxPro ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- ODBC level 1 API functions [ODBC]
- functions [ODBC], API
- ODBC API functions [ODBC]
- level 1 API functions [ODBC]
- API functions [ODBC]
- core level API functions [ODBC]
- level 2 API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 512f9cee-ffad-439b-b612-b49c34c32658
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 26bb1f24a7dbb307d3048b8ec2a8ae293ddbe7ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298104"
---
# <a name="odbc-functions-and-the-visual-foxpro-odbc-driver"></a>Функции ODBC и драйвер ODBC для Visual FoxPro
Темы в этом разделе предоставляют краткое резюме функций ODBC API и любых визуальных деталей FoxPro.  
  
> [!NOTE]  
>  Для получения общей информации [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md) о функциях ODBC см.  
  
 Функции API ODBC были разделены на три основные категории: функции API core Level, функции API уровня 1 и API уровня 2.  
  
> [!NOTE]  
>  Некоторые функции ведут себя по-разному в зависимости от того, определяется ли источник данных как подключение к каталогу [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md) (.dbf файлов) или к [базе данных](../../odbc/microsoft/visual-foxpro-terminology.md) Visual FoxPro (.dbc file). Некоторые операции поддерживаются только для подключения к базе данных.  
  
## <a name="core-level-api-support"></a>Поддержка API базового уровня  
 Функции API уровня ODBC core приведены в следующей таблице. Все эти функции поддерживаются Visual FoxPro ODBC Driver.  
  
|||  
|-|-|  
|[СЗЛАллокКоннект](../../odbc/microsoft/sqlallocconnect-visual-foxpro-odbc-driver.md)|[SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md)|  
|[СЗЛАллокЕнв](../../odbc/microsoft/sqlallocenv-visual-foxpro-odbc-driver.md)|[SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md)|  
|[СЗЛАлокСтмт](../../odbc/microsoft/sqlallocstmt-visual-foxpro-odbc-driver.md)|[СЗЛФриКоннект](../../odbc/microsoft/sqlfreeconnect-visual-foxpro-odbc-driver.md)|  
|[SQLBindCol](../../odbc/microsoft/sqlbindcol-visual-foxpro-odbc-driver.md)|[СЗЛФриЕнв](../../odbc/microsoft/sqlfreeenv-visual-foxpro-odbc-driver.md)|  
|[SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)|[Функция SQLFreeStmt](../../odbc/microsoft/sqlfreestmt-visual-foxpro-odbc-driver.md)|  
|[СЗЛКолАтрибуты](../../odbc/microsoft/sqlcolattributes-visual-foxpro-odbc-driver.md)|[SQLGetCursorName](../../odbc/microsoft/sqlgetcursorname-visual-foxpro-odbc-driver.md)|  
|[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)|[SQLNumResultCols](../../odbc/microsoft/sqlnumresultcols-visual-foxpro-odbc-driver.md)|  
|[SQLDescribeCol](../../odbc/microsoft/sqldescribecol-visual-foxpro-odbc-driver.md)|[SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md)|  
|[СЗЛДИСКоннект](../../odbc/microsoft/sqldisconnect-visual-foxpro-odbc-driver.md)|[SQLRowCount](../../odbc/microsoft/sql-row-count-visual-foxpro-odbc-driver.md)|  
|[Sqlerror](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)|[СЗЛСетКурсОрНамейм](../../odbc/microsoft/sqlsetcursorname-visual-foxpro-odbc-driver.md)|  
|[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)|[СЗЛТрансакт](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)|  
  
## <a name="level-1-api-support"></a>Поддержка API уровня 1  
 Функции API уровня ODBC 1 перечислены в следующей таблице. Все эти функции полностью или частично поддерживаются Visual FoxPro ODBC Driver.  
  
|||  
|-|-|  
|[SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)|[SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md)|  
|[SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)|[SQLParamData](../../odbc/microsoft/sqlparamdata-visual-foxpro-odbc-driver.md)|  
|[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)|[SQLPutData](../../odbc/microsoft/sqlputdata-visual-foxpro-odbc-driver.md)|  
|[СЗЛГетКоннектОпция](../../odbc/microsoft/sqlgetconnectoption-visual-foxpro-odbc-driver.md)|[СЗЛЕтКоннектОпция](../../odbc/microsoft/sqlsetconnectoption-visual-foxpro-odbc-driver.md)|  
|[SQLGetData](../../odbc/microsoft/sqlgetdata-visual-foxpro-odbc-driver.md)|[СЗЛСетСтмтOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md)|  
|[SQLGetFunctions](../../odbc/microsoft/sqlgetfunctions-visual-foxpro-odbc-driver.md)|[SQLSpecialColumns](../../odbc/microsoft/sqlspecialcolumns-visual-foxpro-odbc-driver.md)|  
|[SQLGetInfo](../../odbc/microsoft/sqlgetinfo-visual-foxpro-odbc-driver.md)|[SQLStatistics](../../odbc/microsoft/sqlstatistics-visual-foxpro-odbc-driver.md)|  
|[СЗЛГетСтмтOption](../../odbc/microsoft/sqlgetstmtoption-visual-foxpro-odbc-driver.md)|[SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)|  
  
## <a name="level-2-api-support"></a>Поддержка API уровня 2  
 Следующие функции API уровня ODBC 2 полностью или частично поддерживаются:  
  
-   [Источники данных S'LData](../../odbc/microsoft/sqldatasources-visual-foxpro-odbc-driver.md)  
  
-   [SQLDrivers](../../odbc/microsoft/sqldrivers-visual-foxpro-odbc-driver.md)  
  
-   [Sqlextendedfetch](../../odbc/microsoft/sqlextendedfetch-visual-foxpro-odbc-driver.md)  
  
-   [SQLMoreResults](../../odbc/microsoft/sqlmoreresults-visual-foxpro-odbc-driver.md)  
  
-   [SQLNumParams](../../odbc/microsoft/sqlnumparams-visual-foxpro-odbc-driver.md)  
  
-   [СЗЛПарамОпции](../../odbc/microsoft/sqlparamoptions-visual-foxpro-odbc-driver.md)  
  
-   [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md)  
  
-   [функция SQLSetPos;](../../odbc/microsoft/sqlsetpos-visual-foxpro-odbc-driver.md)  
  
-   [SLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) (частичная поддержка)  
  
 Следующие функции API уровня 2 не поддерживаются:  
  
-   SQLBrowseConnect  
  
-   SQLColumnPrivileges  
  
-   SQLDescribeParam  
  
-   SQLForeignKeys  
  
-   SQLNativeSql  
  
-   SQLProcedureColumns  
  
-   SQLProcedures  
  
-   SQLTablePrivileges
