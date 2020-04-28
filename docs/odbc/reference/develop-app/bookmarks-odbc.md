---
title: Закладки (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8273c82b918024417e613ea44a2d26bafaf7d76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306325"
---
# <a name="bookmarks-odbc"></a>Закладки (ODBC)
Закладка представляет собой значение, используемое для идентификации строки данных. Содержание значения закладки понятно только драйверу или источнику данных. Например, оно может быть простым (номером строки) или сложным (адрес на диске). Закладки в ODBC немного отличаются от закладок в реальных книгах. В реальной книге средство чтения помещает закладку на указанную страницу, а затем ищет эту закладку, чтобы вернуться на страницу. В ODBC приложение запрашивает закладку для конкретной строки, сохраняет ее и передает обратно курсору для возврата к строке. Таким образом, закладки в ODBC похожи на запись номера страницы, ее запоминание и последующем поиске.  
  
 Чтобы определить поддержку закладок драйвером, приложение вызывает **SQLGetInfo** с параметром SQL_BOOKMARK_PERSISTENCE. Биты в этом значении описывают, какие операции закрываются, например, должны ли закладки оставаться действительными после закрытия курсора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы закладок](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Извлечение закладок](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Прокрутка по закладкам](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Обновление, удаление или выборка по закладкам](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Сравнение закладок](../../../odbc/reference/develop-app/comparing-bookmarks.md)
