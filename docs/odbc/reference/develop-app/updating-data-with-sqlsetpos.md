---
title: Обновление данных с помощью S'LSetPos Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16476a1e1007905f34ec2e70ce6032eb8d81fe7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286164"
---
# <a name="updating-data-with-sqlsetpos"></a>Обновление данных с помощью SQLSetPos
Приложения могут обновлять или удалять любую строку в строке с **помощью S'LSetPos.** Вызов **S'LSetPos** является удобной альтернативой построению и исполнинию оператора S'L. Это позволяет драйверу ODBC поддерживать позиционированные обновления, даже если источник данных не поддерживает позиционированные операторы S'L. Это часть парадигмы достижения полного доступа к базе данных с помощью функциональных вызовов.  
  
 **SLSetPos** работает на текущем наборе строк и может быть использован только после звонка в **S'LFetchScroll.** Приложение определяет число строки для обновления, удаления или вставки, и драйвер извлекает новые данные для этой строки из буферов строки. **Кроме** того, можно использовать определенный ряд в качестве текущей строки или для обновления определенной строки в строке из источника данных.  
  
 Размер Rowset устанавливается вызовом в **S'LSetStmtAttr** с аргументом *атрибута* SQL_ATTR_ROW_ARRAY_SIZE. Однако, однако, только после звонка в **S'LFetch** или **S'LFetchScroll**использует новый размер строки. **SQLSetPos** Например, если размер строки изменен, то называется **S'LSetPos,** а затем вызывается **S'LFetch** или **S'LFetchScroll,** а призыв к **S'LSetPos** использует старый размер строки, в то время как **S'LFetch** или **S'LFetchScroll** использует новый размер строки.  
  
 Первая строка в наборе строк имеет номер 1. Аргумент *RowNumber* в **S'LSetPos** должен определить строку в строке; то есть, его значение должно находиться в диапазоне между 1 и числостроки, которые были совсем недавно извлечены (которые могут быть меньше, чем размер строки). Если *rowNumber* равен 0, операция применяется к каждой строке в строке.  
  
 Поскольку большинство взаимодействий с реляционными базами данных осуществляется с помощью S'L, **S'LSetPos** не пользуется широкой поддержкой. Тем не менее, водитель может легко подражать ему, сооружая и исполняя заявление **UPDATE** или **DELETE.**  
  
 Чтобы определить, какие операции поддерживает **S'LSetPos,** приложение вызывает **s'LGetInfo** с SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 вариантинформации (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Удаление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
