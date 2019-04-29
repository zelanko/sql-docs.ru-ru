---
title: SQLGetTypeInfo (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05cc6dc2647b5297b8d7176cd4bc70261b78cb71
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181412"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Возвращает сведения о типах данных, поддерживаемых источником данных. Драйвер возвращает сведения в результирующем наборе SQL. В следующей таблице перечислены типы данных ODBC и соответствующие типы данных Visual FoxPro.  
  
|Тип ODBC|Тип Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Не поддерживается. Отсутствует тип Visual FoxPro 64-разрядной.|  
|SQL_BIT|Логические|  
|SQL_CHAR|Символ|  
|SQL_DATE|Дата|  
|SQL_DECIMAL|Numeric|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Целочисленный|  
|SQL_LONGVARBINARY|MEMO (двоичный)|  
|SQL_LONGVARCHAR|MEMO|  
|SQL_NUMERIC|Числовые *, валюты, в число с плавающей запятой|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Целочисленный|  
|SQL_TIME|Не поддерживается. Имеется не Visual FoxPro *время* типа.|  
|SQL_TIMESTAMP|Datetime|  
|SQL_TINYINT|Целочисленный|  
|SQL_VARBINARY|MEMO (двоичный) *, общие|  
|SQL_VARCHAR|Символ|  
  
 * Тип по умолчанию  
  
 Дополнительные сведения о типах данных Visual FoxPro, см. в разделе [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Дополнительные сведения об этой функции см. в разделе [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) в *Справочник по программированию ODBC*.
