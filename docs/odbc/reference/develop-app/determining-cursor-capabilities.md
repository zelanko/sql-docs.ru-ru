---
title: Определение возможностей курсора | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 14715e40cd99f3f1a03c2ae19e825705a8376e30
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68040005"
---
# <a name="determining-cursor-capabilities"></a>Определение возможностей курсора
Четыре варианта в **SQLGetInfo** описывают, какие типы курсоров поддерживаются и какие возможности:  
  
-   SQL_CURSOR_SENSITIVITY. Указывает, является ли конфиденциальным для изменения, внесенные другим курсором курсора.  
  
-   SQL_SCROLL_OPTIONS. Список типов поддерживаемых курсора (однопроходный, статический, набором, динамические или смешанный). Все источники данных должны поддерживать однопроходные курсоры.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 (в зависимости от типа курсора). Перечисляет типы выборки, Прокручиваемые курсоры. Биты в возвращаемом значении соответствуют типам выборки в **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 или SQL_STATIC_CURSOR_ATTRIBUTES2 (в зависимости от типа курсора). Перечислены ли статические и управляемые набором ключей курсоры можно определить свои собственные обновления, удаления и вставки.  
  
 Приложение может определить возможности курсора во время выполнения путем вызова **SQLGetInfo** с этими параметрами. Обычно это делается, универсальные приложения. Возможности курсора также можно определить во время разработки приложения и их использование жестко в приложение. Это часто осуществляется по вертикали и пользовательских приложений, но также можно сделать, универсальных приложений, использующих реализации курсор на стороне клиента, например, библиотека курсоров ODBC.
