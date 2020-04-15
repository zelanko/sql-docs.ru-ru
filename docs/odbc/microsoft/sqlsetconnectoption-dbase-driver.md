---
title: S'LSetConnectOption (драйвер dBASE) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], dBASE Driver
ms.assetid: b1924c33-6820-4566-b716-6897807edd0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32bfb4755d308706372c0d863f8246631c122f21
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301525"
---
# <a name="sqlsetconnectoption-dbase-driver"></a>SQLSetConnectOption (драйвер для dBASE)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах dBASE. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно установить на SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Однако драйвер не препятствует обновлению, если SQL_ACCESS_MODE настроена на SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер dBASE поддерживает только SQL_AUTOCOMMIT, устанавливаемый в ON (состояние по умолчанию), поскольку он не поддерживает транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|
