---
title: Диагностика для рабочего стола, базы данных драйверы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6c21af2ef3f47c05aacf4b47673ab42a170f506
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128072"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Диагностика драйверов для баз данных на настольном компьютере
Все ошибки и предупреждения не проверяются и частично проверен диспетчером драйверов обрабатываются драйвером. Драйвер также сопоставляет собственного ошибок или ошибок, возвращаемых источником данных, чтобы SQLSTATE. Каждой функции, перечисленные в *Справочник по программированию ODBC* содержит раздел «Диагностика», указывающее условия и сообщения.  
  
 Приложения вызывают **SQLGetDiagRec** для получения SQLSTATE, собственное значение кода ошибки и диагностические сообщения. Вызов **SQLGetDiagField** и указав поле извлекает отдельных полей диагностики. В следующей таблице указан уровень поддержки диагностики идентификаторов.  
  
|DiagIdentifiers|Уровень поддержки|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Не поддерживается|  
|SQL_DIAG_CLASS_ORIGIN|Поддерживается. Всегда «ODBC 3.0 «для версий 3.0 и более поздних версий этот драйвер.|  
|SQL_DIAG_COLUMN_NUMBER|Поддерживается|  
|SQL_DIAG_CURSOR_ROW_COUNT|Не поддерживается|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Не поддерживается|  
|SQL_DIAG_MESSAGE_TEXT|Поддерживается|  
|SQL_DIAG_NATIVE|Поддерживается|  
|SQL_DIAG_NUMBER|Поддерживается|  
|SQL_DIAG_RETURNCODE|Поддерживается, но реализован диспетчером драйверов|  
|SQL_DIAG_ROW_COUNT|Поддерживается|  
|SQL_DIAG_ROW_NUMBER|Поддерживается|  
|SQL_DIAG_SERVER_NAME|Не поддерживается|  
|SQL_DIAG_SQLSTATE|Поддерживается|  
|SQL_DIAG_SUBCLASS_ORIGIN|Поддерживается|
