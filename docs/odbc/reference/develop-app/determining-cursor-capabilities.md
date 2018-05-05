---
title: Определение возможности курсора | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60c84af3a95de609e33072bd876fc9862b6f078c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="determining-cursor-capabilities"></a>Определение возможности курсора
В следующих четырех вариантов **SQLGetInfo** описаны поддерживаемые типы курсоров и каковы возможности:  
  
-   SQL_CURSOR_SENSITIVITY. Указывает, учитывается ли курсор изменений, внесенных другим курсором.  
  
-   SQL_SCROLL_OPTIONS. Список типов поддерживаемых курсора (только вперед, статические, управляемые набором ключей, динамических или смешанный). Все источники данных должны поддерживать однонаправленные курсоры.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 (в зависимости от типа курсора). Список выборки типы, поддерживаемые Прокручиваемые курсоры. Биты в возвращаемом значении соответствуют типам выборки в **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 или SQL_STATIC_CURSOR_ATTRIBUTES2 (в зависимости от типа курсора). Содержит список ли статические и управляемые набором ключей курсоры можно определить собственные обновления, удаления и вставки.  
  
 Приложение может определить возможности курсора во время выполнения путем вызова **SQLGetInfo** с этими параметрами. Обычно это осуществляется универсальные приложения. Возможности курсора также можно определить во время разработки приложений и их использование жестко запрограммированных в приложение. Это обычно делается по вертикали и пользовательских приложений, но также можно сделать, универсальные приложения, используется реализация курсор на стороне клиента, например библиотеку курсоров ODBC.
