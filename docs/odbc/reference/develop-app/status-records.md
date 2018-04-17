---
title: Состояние записи | Документы Microsoft
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
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e748612bf8293a0c7fca29b0baa21c9278e44d15
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="status-records"></a>Состояние записи
Поля в записях состояния содержат сведения о конкретных ошибках и предупреждениях, возвращаемых источником диспетчера драйверов, драйвером или данных, включая SQLSTATE, номер внутренней ошибки, диагностическое сообщение, номер столбца и номер строки. Состояние записи могут создаваться только в том случае, если функция возвращает значение SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA или SQL_STILL_EXECUTING. Полный список полей в записях состояния см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Атрибуты SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Диагностические сообщения](../../../odbc/reference/develop-app/diagnostic-messages.md)
