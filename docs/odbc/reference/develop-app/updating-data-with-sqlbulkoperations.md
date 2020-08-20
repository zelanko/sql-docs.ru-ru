---
description: Обновление данных с помощью SQLBulkOperations
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6c8626a0925d0f30792ed92332c0f96efd23f62e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465538"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Обновление данных с помощью SQLBulkOperations
Приложения могут выполнять операции полного обновления, удаления, выборки или вставки в базовой таблице в источнике данных с помощью вызова **SQLBulkOperations**. Вызов **SQLBulkOperations** является удобной альтернативой созданию и выполнению инструкции SQL. Он позволяет драйверу ODBC поддерживать позиционированные обновления, даже если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигмы достижения полного доступа к базе данных с помощью вызовов функций.  
  
 **SQLBulkOperations** работает с текущим набором строк и может использоваться только после вызова **SQLFetch** или **SQLFetchScroll**. Приложение указывает строки для обновления, удаления или обновления путем кэширования закладок. Драйвер получает новые данные для обновляемых строк или новые данные, вставляемые в базовую таблицу из буферов набора строк.  
  
 Размер набора строк, используемый **SQLBulkOperations** , задается вызовом **SQLSetStmtAttr** с аргументом *атрибута* SQL_ATTR_ROW_ARRAY_SIZE. В отличие от функции **SQLSetPos**, которая использует новый размер набора строк только после вызова **SQLFetch** или **SQLFetchScroll**, **SQLBulkOperations** использует новый размер набора строк после вызова **SQLSetStmtAttr**.  
  
 Так как большинство взаимодействий с реляционными базами данных выполняются с помощью SQL, **SQLBulkOperations** не поддерживается широко. Однако драйвер может легко эмулировать его, создав и выполнив инструкцию **Update**, **Delete**или **INSERT** .  
  
 Чтобы определить, какие операции поддерживает **склбулкоператион** , приложение вызывает **SQLGetInfo** с параметром SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 Information (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Удаление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Вставка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Выборка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
