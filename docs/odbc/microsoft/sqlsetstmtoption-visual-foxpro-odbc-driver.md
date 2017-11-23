---
title: "SQLSetStmtOption (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77cd6f6f8ddd09a011dba2cbbe39c962d78b4574
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Задает параметры, относящиеся к дескриптор инструкции *hstmt*.  
  
|*fOption*|Допустимые значения|Комментарии|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|При попытке задать это *fOption*, драйвер возвращает ошибку: «Драйвер не поддерживает». Visual FoxPro не поддерживает асинхронное выполнение.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN или 32-разрядное значение, обозначающее длину структуры или экземпляра буфера, в которой результат будет привязан столбцов.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Драйвер не допускает SQL_CONCUR_ROWVER, так как Visual FoxPro не поддерживает управление версиями строк, в зависимости от отметки времени.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Драйвер не допускает SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC; в разделе [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) для получения дополнительной информации.|  
|SQL_KEYSET_SIZE|Ошибка: «драйвер не поддерживает»|Visual FoxPro не поддерживает модель курсора keyset.|  
|SQL_MAX_LENGTH|0|При попытке задать это *fOption* значение, драйвер возвращает ошибку «Драйвер не поддерживает».|  
|SQL_MAX_ROWS|0|При попытке задать это *fOption* значение, драйвер возвращает ошибку «Драйвер не поддерживает».|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|При попытке задать это *fOption* значение, драйвер возвращает ошибку «Драйвер не поддерживает».|  
|SQL_RETRIEVE_DATA|SQL_RD_ON SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 в 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Ошибка: «драйвер не поддерживает»||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Дополнительные сведения см. в разделе [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) в *справочнике программиста ODBC*.
