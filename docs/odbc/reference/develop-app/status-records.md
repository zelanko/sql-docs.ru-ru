---
title: "Состояние записи | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eabde5fad5c72cb8d3a662462759c0c342ca4ac2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="status-records"></a>Состояние записи
Поля в записях состояния содержат сведения о конкретных ошибках и предупреждениях, возвращаемых источником диспетчера драйверов, драйвером или данных, включая SQLSTATE, номер внутренней ошибки, диагностическое сообщение, номер столбца и номер строки. Состояние записи могут создаваться только в том случае, если функция возвращает значение SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA или SQL_STILL_EXECUTING. Полный список полей в записях состояния см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Атрибуты SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Диагностические сообщения](../../../odbc/reference/develop-app/diagnostic-messages.md)
