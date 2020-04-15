---
title: СЗЛСетСтмтOption (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb9677a9ccf307be847089c657964d96904eb20b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299404"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Устанавливает параметры, связанные с ручкой оператора, *hstmt.*  
  
|*fOption*|Допустимые значения|Комментарии|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Если вы попытаетесь установить этот *fOption*, водитель возвращает ошибку: "Водитель не способен". Visual FoxPro не поддерживает асинхронное исполнение.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN или 32-битное значение, обозначающее длину структуры или экземпляр буфера, в который будут привязаны столбцы результата.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Водитель не позволяет SQL_CONCUR_ROWVER, потому что Visual FoxPro не имеет строки версии на основе меток времени.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Водитель не позволяет SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC; Для получения дополнительной информации [см.](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md)|  
|SQL_KEYSET_SIZE|Ошибка: "Водитель не способен"|Visual FoxPro не поддерживает модель курсора ключей.|  
|SQL_MAX_LENGTH|0|Если вы попытаетесь установить это значение *fOption,* водитель возвращает ошибку "Водитель не способен".|  
|SQL_MAX_ROWS|0|Если вы попытаетесь установить это значение *fOption,* водитель возвращает ошибку "Водитель не способен".|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Если вы попытаетесь установить это значение *fOption,* водитель возвращает ошибку "Водитель не способен".|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|от 1 до 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Ошибка: "Водитель не способен"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlsetstmtoption-function.md)
