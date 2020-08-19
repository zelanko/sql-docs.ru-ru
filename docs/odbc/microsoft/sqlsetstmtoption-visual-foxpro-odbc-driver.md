---
description: SQLSetStmtOption (драйвер ODBC для Visual FoxPro)
title: SQLSetStmtOption (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.openlocfilehash: c2688a41b660fd12314186fbc270cdc49f16bbe6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421628"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень 1  
  
 Задает параметры, связанные с маркером инструкции, *хстмт*.  
  
|*Параметром fOption*|Допустимые значения|Комментарии|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|При попытке установить этот *параметром fOption*драйвер возвращает ошибку: "драйвер не поддерживается". Visual FoxPro не поддерживает асинхронное выполнение.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN или 32-разрядное значение, указывающее длину структуры или экземпляра буфера, к которому будут привязаны результирующие столбцы.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Драйвер не допускает SQL_CONCUR_ROWVER, так как Visual FoxPro не поддерживает управление версиями строк на основе отметок времени.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Драйвер не допускает SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC; Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) .|  
|SQL_KEYSET_SIZE|Ошибка: "драйвер не поддерживается"|Visual FoxPro не поддерживает модель курсора набора ключей.|  
|SQL_MAX_LENGTH|0|При попытке установить это значение *параметром fOption* драйвер возвращает ошибку "драйвер не поддерживается".|  
|SQL_MAX_ROWS|0|При попытке установить это значение *параметром fOption* драйвер возвращает ошибку "драйвер не поддерживается".|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|При попытке установить это значение *параметром fOption* драйвер возвращает ошибку "драйвер не поддерживается".|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|от 1 до 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Ошибка: "драйвер не поддерживается"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Дополнительные сведения см. в разделе [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) в *справочнике программиста по ODBC*.
