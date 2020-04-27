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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 23db0350f0f7271f85e2bc5c6a9e6c8767443a85
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "81299524"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень 1  
  
 Возвращает сведения о типах данных, поддерживаемых источником данных. Драйвер возвращает сведения в результирующем наборе SQL. В следующей таблице перечислены типы данных ODBC и соответствующий тип данных Visual FoxPro.  
  
|Тип ODBC|Тип Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Не поддерживается. Отсутствует 64-разрядный тип Visual FoxPro.|  
|SQL_BIT|Логические|  
|SQL_CHAR|Символ|  
|SQL_DATE|Дата|  
|SQL_DECIMAL|Числовой|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Целое число|  
|SQL_LONGVARBINARY|МЕМО (двоичный)|  
|SQL_LONGVARCHAR|Memo|  
|SQL_NUMERIC|Числовой *, денежный, float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Целое число|  
|SQL_TIME|Не поддерживается. Тип *времени* Visual FoxPro отсутствует.|  
|SQL_TIMESTAMP|Дата и время|  
|SQL_TINYINT|Целое число|  
|SQL_VARBINARY|MEMO (двоичная) *, общие|  
|SQL_VARCHAR|Символ|  
  
 * Тип по умолчанию  
  
 Дополнительные сведения о типах данных Visual FoxPro см. в разделе [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Дополнительные сведения об этой функции см. в разделе [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) в *справочнике программиста по ODBC*.
