---
title: Диагностика для драйверов настольных баз данных (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 99603c047e77d3cd3e077c1b07c2192eeb65f93c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303485"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Диагностика драйверов для баз данных на настольном компьютере
Все ошибки и предупреждения, которые не проверены или частично проверены менеджером драйвера, обрабатываются водителем. Драйвер также отображает нативные ошибки или ошибки, возвращенные источником данных, в S'LSTATEs. Каждая функция, указанная в *Справке программиста ODBC,* содержит раздел "Диагностика", в котором указаны условия и сообщения.  
  
 Приложения вызываютs **S'LGetDiagRec** для получения S'LSTATE, родного кода ошибки и диагностических сообщений. Вызов **S'LGetDiagField** и указание поля получает отдельные диагностические поля. Уровень поддержки диагностических идентификаторов указан в следующей таблице.  
  
|Диагноидентифицирители|Уровень поддержки|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Не поддерживается|  
|SQL_DIAG_CLASS_ORIGIN|Поддерживается. Всегда "ODBC 3.0" для версий 3.0 и более поздний этот драйвер.|  
|SQL_DIAG_COLUMN_NUMBER|Поддерживается|  
|SQL_DIAG_CURSOR_ROW_COUNT|Не поддерживается|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Не поддерживается|  
|SQL_DIAG_MESSAGE_TEXT|Поддерживается|  
|SQL_DIAG_NATIVE|Поддерживается|  
|SQL_DIAG_NUMBER|Поддерживается|  
|SQL_DIAG_RETURNCODE|Поддерживается, но реализован менеджером драйверов|  
|SQL_DIAG_ROW_COUNT|Поддерживается|  
|SQL_DIAG_ROW_NUMBER|Поддерживается|  
|SQL_DIAG_SERVER_NAME|Не поддерживается|  
|SQL_DIAG_SQLSTATE|Поддерживается|  
|SQL_DIAG_SUBCLASS_ORIGIN|Поддерживается|
