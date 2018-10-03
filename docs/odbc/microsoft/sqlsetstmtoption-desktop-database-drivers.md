---
title: SQLSetStmtOption (драйверы для настольных систем баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d946178453e3db317c92031a34e2a345e9060a8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809622"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (драйверы для баз данных на настольном компьютере)
|*fOption*|Комментарии|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Асинхронная обработка не поддерживается. SQL_ASYNC_ENABLE fOption вернет SQLSTATE S1C00 (драйвер не поддерживает).|  
|SQL_KEYSET_SIZE|Размер набора ключей единственным допустимым равно 0, поскольку одновременно и динамические курсоры не поддерживаются. Если это значение равным любому другому числу, оно будет изменено на 0, и при вызове будет возвращено значение SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменено).|  
|SQL_MAX_ROWS|Размер только допустимый набор строк равен 0, так как драйверы для баз данных Desktop не поддерживает ограничение числа возвращаемых строк. Если это значение равным любому другому числу, оно будет изменено на 0, и при вызове будет возвращено значение SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменено).|  
|SQL_QUERY_TIMEOUT|Не поддерживается.|  
|SQL_ROW_NUMBER|Не поддерживается.|  
|SQL_SIMULATE_CURSOR|Не поддерживается.|
