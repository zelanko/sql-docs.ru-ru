---
title: Прокрутка и извлечение строк (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72d262bf73e69388f65ff281e62235d2d831669e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304205"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Прокрутка и выборка строк (ODBC)
При использовании прокрутки курсора приложения вызывают **S'LFetchScroll,** чтобы расположить курсор и получить строки. **S'LFetchScroll** поддерживает относительную прокрутку (следующий, предыдущий и относительный *n* строки), абсолютную прокрутку (первый, последний и ряд *n)* и позиционирование по закладке. Аргументы *FetchOrientation* и *FetchOffset* в **S'LFetchScroll** указывают, какой набор строк нужно принести, как показано на следующих диаграммах.  
  
 ![Выборка следующего, предыдущего, первого и последнего набора строк](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Выборка следующего, предыдущего, первого и последнего набора строк**  
  
 ![Выборка абсолютных, относительных наборов строк и наборов строк с закладками](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Получение Абсолют, Родственник, и Закладка Rowsets**  
  
 **S'LFetchScroll** позиционирует курсор к указанному ряду и возвращает строки в строке, начиная с этой строки. Если указанный ряд перекрывает конец набора результатов, возвращается частичный ряд. Если указанный ряд перекрывает начало набора результатов, первый ряд в наборе результатов обычно возвращается; для получения [подробной](../../../odbc/reference/syntax/sqlfetchscroll-function.md) информации, см.  
  
 В некоторых случаях приложению может потребоваться позиционировать курсор без получения каких-либо данных. Например, он может захотеть проверить, существует ли строка или просто получить закладку для строки, не приводя другие данные по сети. Для этого он устанавливает атрибут SQL_ATTR_RETRIEVE_DATA оператора на SQL_RD_OFF. Переменная, связанная с столбцой закладки (если таковая имеется) всегда обновляется, независимо от настройки атрибута этого оператора.  
  
 После того, как набор строк был извлечен, приложение может вызвать **S'LSetPos** для размещения в определенной строке в строке или обновить строки в строке. Для получения более подробной информации [Updating Data with SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)об использовании **S'LSetPos**см.  
  
> [!NOTE]  
>  Прокрутка поддерживается в ODBC 2. *x* драйверы по **S'LExtendedFetch**. Для получения дополнительной информации в приложении G: Driver Guidelines for Backward Comatibility можно ознакомиться с [Block Cursors, Scrollable Cursors и обратной совместимости.](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)
