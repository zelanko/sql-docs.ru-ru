---
title: SQLSetStmtOption (для настольных баз данных драйверы) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 765f61337b28e1791d9853bbc26b057375084749
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (драйверы для настольных баз данных)
|*fOption*|Комментарии|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Асинхронная обработка не поддерживается. Возвращает SQL_ASYNC_ENABLE fOption SQLSTATE S1C00 (драйвер не поддерживает).|  
|SQL_KEYSET_SIZE|Размер набора ключей только допустимые равно 0, поскольку одновременно и динамические курсоры не поддерживаются. Если это значение равно любому другому числу, он будет изменено на 0, и при вызове будет возвращено значение SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменено).|  
|SQL_MAX_ROWS|Размер только допустимый набор строк равно 0, поскольку драйверы системной базы данных не поддерживают ограничение числа возвращаемых строк. Если это значение равно любому другому числу, он будет изменено на 0, и при вызове будет возвращено значение SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменено).|  
|SQL_QUERY_TIMEOUT|Не поддерживается.|  
|SQL_ROW_NUMBER|Не поддерживается.|  
|SQL_SIMULATE_CURSOR|Не поддерживается.|
