---
title: Аргументы функции Юникода | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3caa5feb387a7acdfa682f048bf77f2d999b560
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305802"
---
# <a name="unicode-function-arguments"></a>Аргументы функции Юникода
Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает версии ANSI и Юникод для всех функций, которые принимают указатели на символьные строки или указатель SQLPOINTER в своих аргументах. Функции Юникода реализованы в виде функции (с суффиксом *W*), а не как макросы. Функции ANSI (который можно вызывать с или без суффикса *A*) аналогичны текущей функций ODBC API.  
  
## <a name="remarks"></a>Примечания  
 Функции Юникода, которые всегда возвращают или принимают строки или длина аргументы передаются как число символов. Для функций, возвращающих сведения о длине данных server отображаемый размер и точность описаны в символах. Когда длиной (размер передачи данных) может ссылаться на строку или нестроковых данных, длина описан в длины октет. Например **SQLGetInfoW** по-прежнему займет с длиной, как число байт, но **SQLExecDirectW** будет использовать количество символов.  
  
 Число символов ссылается на число байтов (октетов) для функции ANSI и количество WCHAR (16-разрядных слова) для функции ЮНИКОДА. В частности последовательности двухбайтовая кодировка (DBCS) или последовательность многобайтовых символов (MBCS) может состоять из нескольких байтов. Последовательность символов Юникода UTF-16 может состоять из нескольких WCHARs.  
  
 Ниже приведен список функций ODBC API, которые поддерживают версии Unicode (W) и ANSI (A):  
  
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
  
 Ниже приведен список функций ODBC установщика и ODBC Translator, которые поддерживают версии Unicode (W) и ANSI (A):  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  Устаревшие функции имеют поддержку сопоставления Unicode-ANSI, так как ODBC 3 *.x* диспетчера драйверов поддерживает перекомпиляции ODBC 2. *x* приложений при помощи ЮНИКОДА **#define**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения на базе Юникода](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Сопоставление функции в диспетчере драйверов](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
