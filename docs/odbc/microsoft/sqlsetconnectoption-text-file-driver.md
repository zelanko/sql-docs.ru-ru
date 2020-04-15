---
title: S'LSetConnectOption (Драйвер текстовых файлов) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306139"
---
# <a name="sqlsetconnectoption-text-file-driver"></a>SQLSetConnectOption (драйвер для текстовых файлов)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах, специфийных для драйверов текста. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно установить на SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Однако драйвер не препятствует обновлению, если SQL_ACCESS_MODE настроена на SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер текста поддерживает только SQL_AUTOCOMMIT, устанавливаемых в ON (состояние по умолчанию), поскольку они не поддерживают транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|
