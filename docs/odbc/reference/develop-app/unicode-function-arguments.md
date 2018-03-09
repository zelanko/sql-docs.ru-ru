---
title: "Аргументы функции Юникода | Документы Microsoft"
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
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5675d39ff68b3ddd9231a90a54fd19793bd829be
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-function-arguments"></a>Аргументы функции Юникода
Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает версии ANSI или Юникод все функции, принимающие указатели на символьные строки или указатель SQLPOINTER в качестве аргумента. Функции Юникода реализованы в виде функции (с помощью суффикса *W*), а не как макросы. Функции ANSI (который можно вызывать с или без суффикса *A*) идентичны функциям API-интерфейса ODBC.  
  
## <a name="remarks"></a>Remarks  
 Функции Юникода, которые всегда возвращают или принимают строки или длина аргументы передаются как число символов. Для функций, возвращающих сведения о длине данных server отображаемый размер и точность описаны в символах. Когда длину (размер передачи данных) может ссылаться на строку или нестроковые данные, длина описан в длины октет. Например **SQLGetInfoW** будет занимать с длиной, как число байт, но **SQLExecDirectW** будет использоваться число символов.  
  
 Число символов ссылается на число байт (октетов) для функции ANSI и число WCHAR (16-разрядных слов) для функции ЮНИКОДА. В частности последовательность двухбайтовых символов (DBCS) или последовательность многобайтовых символов (MBCS) могут состоять из нескольких байтов. Последовательность символов Юникод UTF-16 может состоять из нескольких WCHARs.  
  
 Ниже приведен перечень функций ODBC API, которые поддерживают Юникод (W) и ANSI (A) версии:  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagField**|  
|**SQLColAttribute**|**SQLGetDiagRec**|  
|**SQLColAttributes**|**SQLGetInfo**|  
|**SQLColumnPrivileges**|**SQLGetStmtAttr**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
  
 Ниже приведен список функций ODBC установщика и преобразователь ODBC, поддерживающие Юникод (W) и ANSI (A) версии.  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**Трансляции SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]  
>  Устаревшие функции имеют поддержку сопоставления Unicode-ANSI, так как ODBC 3*.x* поддерживает диспетчер драйверов ODBC 2 перекомпиляции. *x* приложений с помощью ЮНИКОДА **#define**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения на базе Юникода](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Сопоставление функции в диспетчере драйверов](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
