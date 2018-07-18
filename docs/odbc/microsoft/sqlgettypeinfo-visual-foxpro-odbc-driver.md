---
title: SQLGetTypeInfo (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bbf3983ccdeb2c320f4776d608b73e362f0a479
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904309"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Возвращает сведения о типах данных, поддерживаемых источником данных. Драйвер возвращает сведения в результирующем наборе SQL. В следующей таблице перечислены типы данных ODBC и соответствующие типы данных Visual FoxPro.  
  
|Тип ODBC|Тип Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Не поддерживается. Отсутствует тип Visual FoxPro 64-разрядной.|  
|SQL_BIT|Логические|  
|SQL_CHAR|Символ|  
|SQL_DATE|Дата|  
|SQL_DECIMAL|Числовой|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Целочисленный|  
|SQL_LONGVARBINARY|MEMO (двоичный)|  
|SQL_LONGVARCHAR|MEMO|  
|SQL_NUMERIC|Число с плавающей запятой числовые *, денежных единиц|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Целочисленный|  
|SQL_TIME|Не поддерживается. Нет не Visual FoxPro *время* типа.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Целочисленный|  
|SQL_VARBINARY|MEMO (двоичный) *, общие|  
|SQL_VARCHAR|Символ|  
  
 * Тип по умолчанию  
  
 Дополнительные сведения о типах данных Visual FoxPro см. в разделе [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Дополнительные сведения об этой функции см. в разделе [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) в *справочнике программиста ODBC*.
