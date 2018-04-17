---
title: Обновление данных с помощью SQLSetPos | Документы Microsoft
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
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d23f0292665d7e1cfbd4ce0c32e5cf254e8e4fb3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="updating-data-with-sqlsetpos"></a>Обновление данных с помощью SQLSetPos
Приложения могут обновлять или удалять любую строку набора строк с **SQLSetPos**. Вызов **SQLSetPos** является удобной альтернативой созданию и выполнению инструкции SQL. Она позволяет драйверу ODBC поддерживают позиционированные обновления даже в том случае, если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигма достижения всей базы данных access с помощью вызовов функций.  
  
 **SQLSetPos** работает с текущим набором строк и может использоваться только после вызова **SQLFetchScroll**. Приложение указывает номер строки для обновления, удаления или вставки, а драйвер извлекает новые данные для этой строки из набора строк буферов. **SQLSetPos** может также использоваться для обозначения указанной строки как текущую строку или обновить конкретной строки в наборе строк из источника данных.  
  
 Размер набора строк устанавливается вызовом **SQLSetStmtAttr** с *атрибута* аргумент SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** использует новый размер набора строк, однако только после вызова **SQLFetch** или **SQLFetchScroll**. Например, если изменяется размер набора строк **SQLSetPos** вызывается и затем **SQLFetch** или **SQLFetchScroll** вызывается и вызов **SQLSetPos** использует старый размер набора строк при **SQLFetch** или **SQLFetchScroll** использует новый размер набора строк.  
  
 Первая строка в наборе строк имеет номер 1. *RowNumber* аргумент в **SQLSetPos** должен определять строку в наборе строк; то есть его значение должно быть в диапазоне от 1 до номера строк, которые недавно были извлечены (который может быть меньше, чем размер набора строк). Если *RowNumber* равно 0, операция применяется к каждой строки в наборе строк.  
  
 Поскольку большинство взаимодействие с реляционными базами данных выполняется с помощью SQL, **SQLSetPos** широко не поддерживается. Тем не менее, драйвер может легко эмулировать его по созданию и выполнению **обновление** или **удалить** инструкции.  
  
 Чтобы определить, какие операции **SQLSetPos** поддерживает, приложение вызывает **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ ATTRIBUTES1, или параметр SQL_STATIC_CURSOR_ATTRIBUTES1 сведения (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Удаление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
