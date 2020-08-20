---
description: SQLGetTypeInfo (драйвер ODBC для Visual FoxPro)
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
ms.openlocfilehash: e24f506f1134e9191e370971795a23bbbb3bd380
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500183"
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
|SQL_BIT|Логический|  
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
