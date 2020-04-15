---
title: СЗЛГЕтТипИнфо (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299524"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Возвращает информацию о типах данных, поддерживаемых источником данных. Водитель возвращает информацию в наборе результатов S'L. В следующей таблице перечислены типы данных ODBC и соответствующий тип данных Visual FoxPro.  
  
|Тип ODBC|Визуальный тип FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Не поддерживается. Существует не 64-битный визуальный тип FoxPro.|  
|SQL_BIT|Логические|  
|SQL_CHAR|Знак|  
|SQL_DATE|Дата|  
|SQL_DECIMAL|Числовой|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Целое число|  
|SQL_LONGVARBINARY|Памятка (двоичный)|  
|SQL_LONGVARCHAR|Memo|  
|SQL_NUMERIC|Число, Валюта, Поплавок|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Целое число|  
|SQL_TIME|Не поддерживается. Существует не визуальный тип *времени* FoxPro.|  
|SQL_TIMESTAMP|Дата и время|  
|SQL_TINYINT|Целое число|  
|SQL_VARBINARY|Памятка (двоичная)|  
|SQL_VARCHAR|Знак|  
  
 Тип по умолчанию  
  
 Для получения дополнительной информации о типах данных Visual FoxPro [см.](../../odbc/microsoft/create-table-sql-command.md) Для получения более подробной информации об этой *ODBC Programmer's Reference*функции, [см.](../../odbc/reference/syntax/sqlgettypeinfo-function.md)
