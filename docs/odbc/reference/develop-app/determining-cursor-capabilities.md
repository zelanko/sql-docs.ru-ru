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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 984ad8302f2e1695c8df84a64a18042f4cc9e364
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305885"
---
# <a name="determining-cursor-capabilities"></a>Определение возможностей курсора
Следующие четыре параметра в **SQLGetInfo** описывают поддерживаемые типы курсоров и их возможности:  
  
-   SQL_CURSOR_SENSITIVITY. Указывает, является ли курсор чувствительным к изменениям, внесенным другим курсором.  
  
-   SQL_SCROLL_OPTIONS. Перечисляет поддерживаемые типы курсоров (только однопроходные, статические, управляемые набором ключей, динамические или смешанные). Все источники данных должны поддерживать однопроходные курсоры.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 (в зависимости от типа курсора). Перечисляет типы выборки, поддерживаемые прокручиваемыми курсорами. Биты в возвращаемом значении соответствуют типам выборки в **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 или SQL_STATIC_CURSOR_ATTRIBUTES2 (в зависимости от типа курсора). Показывает, могут ли статические и управляемые набором ключей курсоры обнаруживать свои собственные обновления, удаления и вставки.  
  
 Приложение может определить возможности курсора во время выполнения, вызвав **SQLGetInfo** с этими параметрами. Обычно это делается универсальными приложениями. Возможности курсора также можно определить во время разработки приложения, а их использование жестко запрограммировано в приложении. Обычно это делается с помощью вертикальных и пользовательских приложений, но их также можно выполнять с помощью универсальных приложений, использующих реализацию курсора на стороне клиента, такую как библиотека курсоров ODBC.
