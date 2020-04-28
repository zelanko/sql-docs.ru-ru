---
title: SQLSetConnectOption (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Text File Driver
- text file driver [ODBC], SQLSetConnectOption
ms.assetid: b631a20c-2f60-4102-a61d-93b8780a4620
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6442134086ea6fe15b393b87d6c80019a076be2a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306139"
---
# <a name="sqlsetconnectoption-text-file-driver"></a>SQLSetConnectOption (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверам текстовых файлов. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Параметром fOption|Добавление примечаний|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE параметром fOption можно задать как SQL_MODE_READ_ONLY, так и SQL_MODE_READ_WRITE. Однако драйвер не запрещает обновление, если для SQL_ACCESS_MODE установлено значение SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер текста поддерживает только SQL_AUTOCOMMIT, для которых задано значение ON (состояние по умолчанию), так как они не поддерживают транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|
