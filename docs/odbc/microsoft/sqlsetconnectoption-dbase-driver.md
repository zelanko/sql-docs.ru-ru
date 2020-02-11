---
title: SQLSetConnectOption (драйвер для dBASE) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9f2fc32287df9da61d8eabc1b22445d19a0f027
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090858"
---
# <a name="sqlsetconnectoption-dbase-driver"></a>SQLSetConnectOption (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу dBASE. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Параметром fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE параметром fOption можно задать как SQL_MODE_READ_ONLY, так и SQL_MODE_READ_WRITE. Однако драйвер не запрещает обновление, если для SQL_ACCESS_MODE установлено значение SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер dBASE поддерживает только SQL_AUTOCOMMIT, для которых установлено значение ON (состояние по умолчанию), так как оно не поддерживает транзакции.|  
|SQL_CURRENT_QUALIFIER| Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE| Поддерживается.|  
|SQL_OPT_TRACEFILE| Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|
