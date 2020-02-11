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
ms.openlocfilehash: d2895ec765df3910dbbaa1e76ba1579e4afe5cca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091650"
---
# <a name="updating-data-with-sqlsetpos"></a>Обновление данных с помощью SQLSetPos
Приложения могут обновлять или удалять любую строку в наборе строк с помощью функции **SQLSetPos**. Вызов **SQLSetPos** — это удобная альтернатива созданию и выполнению инструкции SQL. Он позволяет драйверу ODBC поддерживать позиционированные обновления, даже если источник данных не поддерживает позиционированные инструкции SQL. Он является частью парадигмы достижения полного доступа к базе данных с помощью вызовов функций.  
  
 Функция **SQLSetPos** работает с текущим набором строк и может использоваться только после вызова **SQLFetchScroll**. Приложение указывает номер строки для обновления, удаления или вставки, а драйвер получает новые данные для этой строки из буферов набора строк. Функцию **SQLSetPos** можно также использовать для обозначения указанной строки в качестве текущей строки или обновления определенной строки в наборе строк из источника данных.  
  
 Размер набора строк задается вызовом **SQLSetStmtAttr** с аргументом *атрибута* SQL_ATTR_ROW_ARRAY_SIZE. Однако функция **SQLSetPos** использует новый размер набора строк только после вызова **SQLFetch** или **SQLFetchScroll**. Например, если изменяется размер набора строк, вызывается функция **SQLSetPos** , затем вызывается **SQLFetch** или **SQLFetchScroll** , а в вызове **SQLSetPos** используется старый размер набора строк, а **SQLFetch** или **SQLFetchScroll** использует новый размер набора строк.  
  
 Первая строка в наборе строк имеет номер 1. Аргумент *RowNumber* в **SQLSetPos** должен указывать строку в наборе строк; Это значит, что его значение должно находиться в диапазоне от 1 до количества недавно выбранных строк (что может быть меньше размера набора строк). Если параметр *RowNumber* имеет значение 0, операция применяется к каждой строке в наборе строк.  
  
 Так как большинство взаимодействий с реляционными базами данных выполняются с помощью SQL, функция **SQLSetPos** не поддерживается широко. Однако драйвер может легко эмулировать его, создав и выполнив инструкцию **Update** или **Delete** .  
  
 Чтобы определить, какие операции поддерживает функция **SQLSetPos** , приложение вызывает **SQLGetInfo** с параметром SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 Information (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Удаление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
