---
title: "Диагностика для рабочего стола, базы данных драйверы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 432d311b1f55ff636e8c0b6fedb28509e3d9e6ed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

