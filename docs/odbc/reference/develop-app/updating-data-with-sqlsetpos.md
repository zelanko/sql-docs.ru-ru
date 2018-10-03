---
title: Обновление данных с помощью SQLSetPos | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1c31ef622281b4f52f62ca3867c5afa7dcae8ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680792"
---
# <a name="updating-data-with-sqlsetpos"></a>Обновление данных с помощью SQLSetPos
Приложения могут обновлять или удалять любую строку набора строк с **SQLSetPos**. Вызов **SQLSetPos** является удобной альтернативой созданию и выполнению инструкции SQL. Это позволяет драйверу ODBC поддерживают позиционированные обновления даже в том случае, если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигма достижения всей базы данных access посредством вызовов функций.  
  
 **SQLSetPos** оперирует текущего набора строк и может использоваться только после вызова **SQLFetchScroll**. Приложение указывает номер строки для обновления, удаления или вставки и драйвер получает новые данные для этой строки из набора строк буферов. **SQLSetPos** может также использоваться для назначения определенной строки в качестве текущей строки или обновить отдельную строку в наборе строк из источника данных.  
  
 Размер набора строк устанавливается вызовом **SQLSetStmtAttr** с *атрибут* аргументом атрибута SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** использует новый размер набора строк, однако только после вызова **SQLFetch** или **SQLFetchScroll**. Например, если изменяется размер набора строк **SQLSetPos** вызывается и затем **SQLFetch** или **SQLFetchScroll** вызывается и вызов **SQLSetPos** использует старый размер набора строк при **SQLFetch** или **SQLFetchScroll** использует новый размер набора строк.  
  
 Первая строка в наборе строк имеет номер 1. *RowNumber* аргумента в **SQLSetPos** должен определять строку в наборе строк; то есть его значение должно быть в диапазоне от 1 до числа строк, которые недавно были извлечены (который может быть меньше, чем размер набора строк). Если *RowNumber* равно 0, операция применяется к каждой строки в наборе строк.  
  
 Так как большинство взаимодействие с реляционными базами данных осуществляется с помощью SQL, **SQLSetPos** широко не поддерживается. Тем не менее драйвер можно легко эмулировать его, созданию и выполнению **обновление** или **удалить** инструкции.  
  
 Чтобы определить, какие операции **SQLSetPos** поддерживает, приложение вызывает **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ Атрибутов1, или параметр SQL_STATIC_CURSOR_ATTRIBUTES1 информации (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Удаление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
