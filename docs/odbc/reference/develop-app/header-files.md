---
title: Файлы заголовка Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62364d828e7b1f1ed8c70cae7ae1fc7dc3bc33fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300194"
---
# <a name="header-files"></a>Файлы заголовков
Файл заголовка Sql.h содержит прототипы функций и функций в базовом уровне соответствия интерфейса ODBC. Файл заголовка Sqlext.h содержит прототипы для функций и функций в уровнях соответствия API уровня 1 и уровня 2. Файл заголовка Sqltypes.h содержит определения типов и индикаторы для типов данных S'L.  
  
 Все файлы заголовка содержат **#define,** ODBCVER, который может быть настроен для компилирования приложения или драйвера для различных версий ODBC.  
  
 Чтобы соответствовать ISO CLI и Open Group CLI, файлы заголовка содержат псевдонимы для типов информации, используемых в вызовах в **S'LGetInfo.** В следующей таблице столбца "имя ODBC" указывает имя ODBC для типа информации в [справке ODBC API.](../../../odbc/reference/syntax/odbc-api-reference.md) В столбце "Alias in header file" указывается имя, используемое в ISO CLI и ClI Open Group. Фактическое числовое значение этих имен манифеста одинаково как в ODBC, так и в стандартных CLIs. Эти псевдонимы позволяют приложению или драйверу, соблюдающим стандарты, компилировать с файлами заголовка ODBC *3.x.*  
  
 Эти псевдонимы включают в себя расширение сокращений в названиях ODBC, так что имена более понятны. "MAX" расширен до "MAXIMUM", "LEN" до "LENGTH", "MULT" до "MULTIPLE", "OJ" на "OUTER_JOIN", и "TXN" на "TRANSACTION".  
  
|Название ODBC|Прозвище в файле заголовка|  
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
