---
title: СЗЛСТоConnectOption (Парадокс драйвер) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLSetConnectOption
ms.assetid: 050ee2be-594e-4dbd-af67-8b6aae756cd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06a90a83e2cbf24e6e85a67d961684c230bca924
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301495"
---
# <a name="sqlsetconnectoption-paradox-driver"></a>SQLSetConnectOption (драйвер для Paradox)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах парадокса. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно установить на SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Однако драйвер не препятствует обновлению, если SQL_ACCESS_MODE настроена на SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер Парадокса поддерживает только SQL_AUTOCOMMIT, устанавливаемые в ON (состояние по умолчанию), потому что они не поддерживают транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|
