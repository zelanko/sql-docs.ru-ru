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
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4689c14c5850b99c64379897bebb248f3aea4643
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
