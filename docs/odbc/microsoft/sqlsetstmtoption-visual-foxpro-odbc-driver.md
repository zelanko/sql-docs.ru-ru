---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d7bcecfbd880f53d1067fd68202b62c34fce398
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305822"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Задает параметры, связанные с дескриптор инструкции *hstmt*.  
  
|*fOption*|Допустимые значения|Комментарии|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|При попытке задать это *fOption*, драйвер возвращает ошибку: «Драйвер не поддерживает». Visual FoxPro не поддерживает асинхронное выполнение.|  
|SQL_BIND_TYPE|Значение sql_bind_bind_by_column или 32-разрядное значение, обозначающее длины структуры или экземпляра буфера, в какой результат будет привязан столбцы.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Драйвер не допускает SQL_CONCUR_ROWVER, поскольку Visual FoxPro не поддерживает управление версиями строк, зависимости от меток времени.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Драйвер не поддерживает SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC; см. в разделе [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) Дополнительные сведения.|  
|SQL_KEYSET_SIZE|Ошибка: «Драйвер не поддерживает»|Visual FoxPro не поддерживает модель курсора keyset.|  
|SQL_MAX_LENGTH|0|При попытке задать это *fOption* значение, драйвер возвращает ошибку «Драйвер не поддерживает».|  
|SQL_MAX_ROWS|0|При попытке задать это *fOption* значение, драйвер возвращает ошибку «Драйвер не поддерживает».|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|При попытке задать это *fOption* значение, драйвер возвращает ошибку «Драйвер не поддерживает».|  
|SQL_RETRIEVE_DATA|SQL_RD_ON SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 для 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Ошибка: «Драйвер не поддерживает»||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Дополнительные сведения см. в разделе [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) в *Справочник по программированию ODBC*.
