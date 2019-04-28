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
manager: craigg
ms.openlocfilehash: 8e6d0806a7c3eabd1c6f4cd1836308eba99a6d5a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724369"
---
# <a name="header-files"></a>Файлы заголовков
Файл заголовка Sql.h содержит прототипы функций и компонентов в уровню соответствия базового интерфейса ODBC. Файл заголовка Sqlext.h содержит прототипы функций и возможностей уровня 1 и уровни соответствия API уровня 2. Файл заголовка Sqltypes.h содержит определения типов и индикаторы для типов данных SQL.  
  
 Файлы заголовков, содержащих **#define**, аргумент ODBCVER, приложения или драйвера можно задать компиляцию для разных версий ODBC.  
  
 В соответствии с ISO CLI и интерфейса командной строки откройте группу, файлы заголовков, которые содержат псевдонимы для типов сведений, используемых в вызовах **SQLGetInfo**. В следующей таблице, в столбце «Имя ODBC» указывается имя ODBC для типа данных в [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md). В столбце «Alias в файле заголовка» указывается имя, которое используется в интерфейсе командной строки ISO и откройте интерфейс командной строки группы. Действительное числовое значение из этих имен манифеста является соответствующим образом в ODBC и стандартная CLI. Эти псевдонимы включения соответствующих стандартам приложения или драйвера для компиляции с ODBC 3 *.x* файлы заголовков.  
  
 Таким образом, более понятными имена, эти псевдонимы: расширения сокращения в именах ODBC. «MAX» расширяется «МАКСИМУМ», «Длина» для «Длина», «MULT» для «MULTIPLE», «OJ» для «OUTER_JOIN» и «Транзакций» для «ТРАНЗАКЦИИ»  
  
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
