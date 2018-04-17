---
title: SQLSetConnectOption (драйвера dBASE) | Документы Microsoft
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
- DBase driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], dBASE Driver
ms.assetid: b1924c33-6820-4566-b716-6897807edd0f
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25585d7719eeb615dab2ec3f55c58b240b8e1bbc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetconnectoption-dbase-driver"></a>SQLSetConnectOption (драйвера dBASE)
> [!NOTE]  
>  В этом разделе сведения dBASE специфические для драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно присвоить значение SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Тем не менее драйвер не запрещает обновление, если SQL_ACCESS_MODE равно SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер dBASE поддерживает только SQL_AUTOCOMMIT устанавливается на (состояние по умолчанию), так как он не поддерживает транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|
