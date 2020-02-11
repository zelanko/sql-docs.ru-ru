---
title: Файлы заголовков | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d20f2535038b13eac0b8d5ca20dfa77bfc12588
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139026"
---
# <a name="header-files"></a>Файлы заголовков
Файл заголовка SQL. h содержит прототипы функций и функций в базовом уровне соответствия интерфейсов ODBC. Файл заголовка Sqlext. h содержит прототипы функций и функций уровней соответствия API уровня 1 и уровня 2. Файл заголовка SqlTypes. h содержит определения типов и индикаторы для типов данных SQL.  
  
 Все файлы заголовков содержат **#define**, одбквер, что приложение или драйвер могут быть скомпилированы для разных версий ODBC.  
  
 Для согласования с интерфейсом командной строки ISO и открытия группы CLI файлы заголовков содержат псевдонимы для типов сведений, используемых в вызовах **SQLGetInfo**. В следующей таблице столбец "имя ODBC" указывает имя ODBC для типа сведений в [справочнике по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md). Столбец «псевдоним в файле заголовка» указывает имя, которое используется в интерфейсе командной строки ISO и в интерфейсе командной строки Open Group. Фактическое числовое значение этих имен манифеста одинаково как в ODBC, так и в стандартном CLI. Эти псевдонимы позволяют приложению или драйверу, удовлетворяющему стандартам, компилироваться с файлами заголовков ODBC *3. x* .  
  
 Эти псевдонимы содержат расширения аббревиатур в именах ODBC, чтобы имена были более понятными. "MAX" расширяется до "максимум", "LEN" до "LENGTH", "MULT" на "MULTIPLE", "ОЖ" в "OUTER_JOIN" и "транзакция" в "TRANSACTION".  
  
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
