---
title: SLSetStmtOption (Драйверы базы данных для рабочей стола) Документы Майкрософт
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
ms.openlocfilehash: 69b386aee3f95fd047f72510dce7658130ac7aa5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299414"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (драйверы для баз данных на настольном компьютере)

|*fOption*|Комментарии|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Асинхронная обработка не поддерживается. В SQL_ASYNC_ENABLE fOption вернет S'Lstate S1C00 (Водитель не способен).|  
|SQL_KEYSET_SIZE|Единственный допустимый размер ключа составляет 0, так как смешанные и динамические курсоры не поддерживаются. Если это значение будет установлено на любое другое число, оно будет изменено на 0, и вызов вернется SQL_SUCCESS_WITH_INFO и S'Lstate 01S02 (изменение значения опциона).|  
|SQL_MAX_ROWS|Единственный допустимый размер строки — 0, так как драйверы настольной базы данных не поддерживают ограничение количества возвращенных строк. Если это значение будет установлено на любое другое число, оно будет изменено на 0, и вызов вернется SQL_SUCCESS_WITH_INFO и S'Lstate 01S02 (изменение значения опциона).|  
|SQL_QUERY_TIMEOUT|Не поддерживается.|  
|SQL_ROW_NUMBER|Не поддерживается.|  
|SQL_SIMULATE_CURSOR|Не поддерживается.|
