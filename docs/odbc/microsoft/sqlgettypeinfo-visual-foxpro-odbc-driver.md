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
ms.openlocfilehash: f29be5e03a6cc9c1c91809db2b8ec7c686e90f11
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898630"
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
|SQL_CHAR|Character|  
|SQL_DATE|Дата|  
|SQL_DECIMAL|Числовой|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Целое число|  
|SQL_LONGVARBINARY|МЕМО (двоичный)|  
|SQL_LONGVARCHAR|Получена|  
|SQL_NUMERIC|Числовой *, денежный, float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Целое число|  
|SQL_TIME|Не поддерживается. Тип *времени* Visual FoxPro отсутствует.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Целое число|  
|SQL_VARBINARY|MEMO (двоичная) *, общие|  
|SQL_VARCHAR|Character|  
  
 * Тип по умолчанию  
  
 Дополнительные сведения о типах данных Visual FoxPro см. в разделе [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Дополнительные сведения об этой функции см. в разделе [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) в *справочнике программиста по ODBC*.
