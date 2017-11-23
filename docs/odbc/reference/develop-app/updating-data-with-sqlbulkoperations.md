---
title: "Обновление данных с помощью SQLBulkOperations | Документы Microsoft"
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
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2bcfa39dca534aaa03fe95293b6143180ac9920
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="updating-data-with-sqlbulkoperations"></a>Обновление данных с помощью SQLBulkOperations
Приложения могут выполнять операции массового обновления, удаления, fetch или вставки в базовой таблице в источнике данных с помощью вызова **SQLBulkOperations**. Вызов **SQLBulkOperations** является удобной альтернативой созданию и выполнению инструкции SQL. Она позволяет драйверу ODBC поддерживают позиционированные обновления даже в том случае, если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигма достижения всей базы данных access с помощью вызовов функций.  
  
 **SQLBulkOperations** работает с текущим набором строк и может использоваться только после вызова **SQLFetch** или **SQLFetchScroll**. Приложение указывает строки, которые необходимо обновить, удалить или обновить путем кэширования закладок. Драйвер возвращает новые данные для обновляемых строк или новые данные должны быть вставлены в базовой таблице, из буферов набора строк.  
  
 Размер набора строк, который будет использоваться **SQLBulkOperations** задается путем вызова **SQLSetStmtAttr** с *атрибута* аргумент SQL_ATTR_ROW_ARRAY_SIZE. В отличие от **SQLSetPos**, которая использует новый размер набора строк только после вызова **SQLFetch** или **SQLFetchScroll**, **SQLBulkOperations** использует новый размер набора строк после вызова **SQLSetStmtAttr**.  
  
 Поскольку большинство взаимодействие с реляционными базами данных выполняется с помощью SQL, **SQLBulkOperations** широко не поддерживается. Тем не менее, драйвер может легко эмулировать его по созданию и выполнению **обновление**, **удаление**, или **вставить** инструкции.  
  
 Чтобы определить, какие операции **SQLBulkOperation** поддерживает, приложение вызывает **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1, или параметр SQL_STATIC_CURSOR_ATTRIBUTES1 сведения (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Удаление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Вставка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Выборка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
