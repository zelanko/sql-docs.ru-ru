---
title: Файлы заголовков | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75a2e7bcee4f777a3f0442425c0395be99000668
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="header-files"></a>Заголовочные файлы
Файл заголовка Sql.h содержит прототипы для функций и возможностей в уровень соответствия основной интерфейс ODBC. Файл заголовка Sqlext.h содержит прототипы для функций и возможностей уровня 1 и уровни соответствия API уровня 2. Файл заголовка Sqltypes.h содержит определения типов и индикаторы для типов данных SQL.  
  
 Файлы заголовков, содержащих **#define**, аргумент ODBCVER, скомпилированы для разных версий ODBC можно задать приложения или драйвера.  
  
 В соответствии с ISO CLI и откройте группу CLI, файлы заголовков, которые содержат псевдонимы для типы сведения, используемые в вызовах **SQLGetInfo**. В следующей таблице, столбец «Имя ODBC» указывает имя ODBC для типа данных в [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md). В столбце «Alias в файле заголовка» указывается имя, которое используется в ISO CLI и откройте группу CLI. Действительное числовое значение из этих имен манифеста одинаково в ODBC и стандартная CLI. Эти псевдонимы включения стандартам приложения или драйвера для компиляции с ODBC 3*.x* файлы заголовков.  
  
 Эти псевдонимы: расширения сокращений в именах ODBC, чтобы имена были более понятными. «MAX» расширяется «МАКСИМУМ», «Длина» для «Длина», «MULT» для «Несколько», «OJ» на «OUTER_JOIN» и «Транзакций» для «ТРАНЗАКЦИИ».  
  
|Имя ODBC|Псевдоним в файле заголовка|  
|---------------|--------------------------|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAXIMUM_CATALOG_NAME_LENGTH|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAXIMUM_COLUMN_NAME_LENGTH|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAXIMUM_COLUMNS_IN_GROUP_BY|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAXIMUM_COLUMNS_IN_ORDER_BY|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAXIMUM_COLUMNS_IN_SELECT|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAXIMUM_COLUMNS_IN_TABLE|  
|SQL_MAX_CONCURRENT_ACTIVITIES|SQL_MAXIMUM_CONCURRENT_ACTIVITIES|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAXIMUM_CURSOR_NAME_LENGTH|  
|SQL_MAX_DRIVER_CONNECTIONS|SQL_MAXIMUM_DRIVER_CONNECTIONS|  
|SQL_MAX_IDENTIFIER_LEN|SQL_MAXIMUM_IDENTIFIER_LENGTH|  
|SQL_MAX_SCHEMA_NAME_LEN|SQL_MAXIMUM_SCHEMA_NAME_LENGTH|  
|SQL_MAX_STATEMENT_LEN|SQL_MAXIMUM_STATEMENT_LENGTH|  
|SQL_MAX_TABLE_NAME_LEN|SQL_MAXIMUM_TABLE_NAME_LENGTH|  
|SQL_MAX_TABLES_IN_SELECT|SQL_MAXIMUM_TABLES_IN_SELECT|  
|SQL_MAX_USER_NAME_LEN|SQL_MAXIMUM_USER_NAME_LENGTH|  
|SQL_MULT_RESULT_SETS|SQL_MULTIPLE_RESULT_SETS|  
|SQL_OJ_CAPABILITIES|SQL_OUTER_JOIN_CAPABILITIES|  
|SQL_TXN_CAPABLE|SQL_TRANSACTION_CAPABLE|  
|SQL_TXN_ISOLATION_OPTION|SQL_TRANSACTION_ISOLATION_OPTION|
