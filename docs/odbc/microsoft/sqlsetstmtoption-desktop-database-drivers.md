---
description: SQLSetStmtOption (драйверы для баз данных на настольном компьютере)
title: SQLSetStmtOption (драйверы баз данных для настольных систем) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0696ee98dd88f1c23120ef1d96c6e8d93751f76e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449156"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (драйверы для баз данных на настольном компьютере)

|*Параметром fOption*|Комментарии|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Асинхронная обработка не поддерживается. SQL_ASYNC_ENABLE параметром fOption вернет значение SQLSTATE S1C00 (драйвер не поддерживается).|  
|SQL_KEYSET_SIZE|Единственный допустимый размер набора ключей равен 0, так как смешанные и динамические курсоры не поддерживаются. Если это значение равно любому другому числу, оно будет изменено на 0, а вызов возвратит SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменено).|  
|SQL_MAX_ROWS|Единственный допустимый размер набора строк равен 0, так как драйверы базы данных для настольных систем не поддерживают ограничение числа возвращаемых строк. Если это значение равно любому другому числу, оно будет изменено на 0, а вызов возвратит SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменено).|  
|SQL_QUERY_TIMEOUT|Не поддерживается.|  
|SQL_ROW_NUMBER|Не поддерживается.|  
|SQL_SIMULATE_CURSOR|Не поддерживается.|
