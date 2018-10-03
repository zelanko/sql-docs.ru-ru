---
title: Обновление данных с помощью SQLBulkOperations | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 958514adc02452cdc75a05e7ad28cd31f4e8e0e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723412"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Обновление данных с помощью SQLBulkOperations
Приложения могут выполнять операции массового обновления, удаления, fetch или вставки в базовой таблице в источнике данных с помощью вызова **SQLBulkOperations**. Вызов **SQLBulkOperations** является удобной альтернативой созданию и выполнению инструкции SQL. Это позволяет драйверу ODBC поддерживают позиционированные обновления даже в том случае, если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигма достижения всей базы данных access посредством вызовов функций.  
  
 **SQLBulkOperations** оперирует текущего набора строк и может использоваться только после вызова **SQLFetch** или **SQLFetchScroll**. Приложение указывает строки для обновления, удаления или обновления путем кэширования закладок. Драйвер возвращает новыми данными о обновляемые строки, или новые данные вставляются в базовой таблице, из набора строк буферов.  
  
 Размер набора строк, который будет использоваться **SQLBulkOperations** задается путем вызова **SQLSetStmtAttr** с *атрибут* аргументом атрибута SQL_ATTR_ROW_ARRAY_SIZE. В отличие от **SQLSetPos**, которая использует новый размер набора строк только после вызова **SQLFetch** или **SQLFetchScroll**, **SQLBulkOperations** использует новый размер набора строк после вызова **SQLSetStmtAttr**.  
  
 Так как большинство взаимодействие с реляционными базами данных осуществляется с помощью SQL, **SQLBulkOperations** широко не поддерживается. Тем не менее драйвер можно легко эмулировать его, созданию и выполнению **обновление**, **удалить**, или **вставить** инструкции.  
  
 Чтобы определить, какие операции **SQLBulkOperation** поддерживает, приложение вызывает **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1, или параметр SQL_STATIC_CURSOR_ATTRIBUTES1 информации (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Удаление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Вставка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Выборка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
