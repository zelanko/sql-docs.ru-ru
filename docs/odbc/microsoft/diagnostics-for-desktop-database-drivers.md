---
title: Диагностика для рабочего стола, базы данных драйверы | Документы Microsoft
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
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23e5933bb5a17d4e870e6d50b8821b6407ccd277
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Диагностика для драйверов для настольных баз данных
Все ошибки и предупреждения не проверяются и частично проверяется диспетчером драйверов обрабатываются драйвером. Драйвер также сопоставляет собственного ошибок или ошибок, возвращаемых источником данных, чтобы SQLSTATE. Каждая функция, перечисленных в *справочнике программиста ODBC* содержит раздел «Диагностика», в котором указываются условия и сообщения.  
  
 Приложения вызывают **SQLGetDiagRec** для извлечения SQLSTATE, машинный код ошибки и диагностические сообщения. Вызов **SQLGetDiagField** и указав в поле получает отдельных полей диагностики. В следующей таблице указывается уровень поддержки диагностики идентификаторов.  
  
|DiagIdentifiers|Уровень поддержки|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Не поддерживается|  
|SQL_DIAG_CLASS_ORIGIN|Поддерживается. Всегда «ODBC 3.0» для версий 3.0 и более поздних версий этот драйвер.|  
|SQL_DIAG_COLUMN_NUMBER|Поддерживается|  
|SQL_DIAG_CURSOR_ROW_COUNT|Не поддерживается|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Не поддерживается|  
|SQL_DIAG_MESSAGE_TEXT|Поддерживается|  
|SQL_DIAG_NATIVE|Поддерживается|  
|SQL_DIAG_NUMBER|Поддерживается|  
|SQL_DIAG_RETURNCODE|Поддерживается, но реализовано диспетчером драйверов|  
|SQL_DIAG_ROW_COUNT|Поддерживается|  
|SQL_DIAG_ROW_NUMBER|Поддерживается|  
|SQL_DIAG_SERVER_NAME|Не поддерживается|  
|SQL_DIAG_SQLSTATE|Поддерживается|  
|SQL_DIAG_SUBCLASS_ORIGIN|Поддерживается|
