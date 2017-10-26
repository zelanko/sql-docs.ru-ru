---
title: "Обновление данных с помощью SQLBulkOperations | Документы Microsoft"
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
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75e5f954065c0b41935aa231c85c093d5ee10226
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data-with-sqlbulkoperations"></a>Обновление данных с помощью SQLBulkOperations
Приложения могут выполнять операции массового обновления, удаления, fetch или вставки в базовой таблице в источнике данных с помощью вызова **SQLBulkOperations**. Вызов **SQLBulkOperations** является удобной альтернативой созданию и выполнению инструкции SQL. Она позволяет драйверу ODBC поддерживают позиционированные обновления даже в том случае, если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигма достижения всей базы данных access с помощью вызовов функций.  
  
 **SQLBulkOperations** работает с текущим набором строк и может использоваться только после вызова **SQLFetch** или **SQLFetchScroll**. Приложение указывает строки, которые необходимо обновить, удалить или обновить путем кэширования закладок. Драйвер возвращает новые данные для обновляемых строк или новые данные должны быть вставлены в базовой таблице, из буферов набора строк.  
  
 Размер набора строк, который будет использоваться **SQLBulkOperations** задается путем вызова **SQLSetStmtAttr** с *атрибута* аргумент SQL_ATTR_ROW_ARRAY_SIZE. В отличие от **SQLSetPos**, которая использует новый размер набора строк только после вызова **SQLFetch** или **SQLFetchScroll**, **SQLBulkOperations** использует новый размер набора строк после вызова **SQLSetStmtAttr**.  
  
 Поскольку большинство взаимодействие с реляционными базами данных выполняется с помощью SQL, **SQLBulkOperations** широко не поддерживается. Тем не менее, драйвер может легко эмулировать его по созданию и выполнению **обновление**, **удаление**, или **вставить** инструкции.  
  
 Чтобы определить, какие операции **SQLBulkOperation** поддерживает, приложение вызывает **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1, или параметр SQL_STATIC_CURSOR_ATTRIBUTES1 сведения (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк по закладке с SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Удаление строк по закладке с SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Вставка строк с SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Выборка строк с SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)

