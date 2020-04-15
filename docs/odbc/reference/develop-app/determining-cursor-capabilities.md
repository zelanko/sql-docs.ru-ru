---
title: Определение возможностей курсора (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 984ad8302f2e1695c8df84a64a18042f4cc9e364
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305885"
---
# <a name="determining-cursor-capabilities"></a>Определение возможностей курсора
Следующие четыре варианта в **S'LGetInfo** описывают, какие типы курсоров поддерживаются и каковы их возможности:  
  
-   SQL_CURSOR_SENSITIVITY. Указывает, чувствителен ли курсор к изменениям, внесенным другим курсором.  
  
-   SQL_SCROLL_OPTIONS. Перечисляет поддерживаемые типы курсоров (только вперед, статичны, управляемые ключами, динамические или смешанные). Все источники данных должны поддерживать курсоры только для форвардов.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 (в зависимости от типа курсора). Перечисляет типы извлечений, поддерживаемые прокрутки курсорами. Биты в значении возврата соответствуют типам извлечений в **S'LFetchScroll.**  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 или SQL_STATIC_CURSOR_ATTRIBUTES2 (в зависимости от типа курсора). Перечисляет, могут ли статические курсоры и курсы, управляемые ключами, обнаруживать свои собственные обновления, удаляет и вставлять.  
  
 Приложение может определить возможности курсора во время выполнения, позвонив в **S'LGetInfo** с этими опциями. Обычно это делается с помощью общих приложений. Возможности Cursor также могут быть определены при разработке приложения и их использовании жестко закодированных в приложении. Обычно это делается вертикальными и пользовательскими приложениями, но также может быть сделано с помощью общих приложений, которые используют реализацию курсора клиентской стороны, такие как библиотека курсора ODBC.
