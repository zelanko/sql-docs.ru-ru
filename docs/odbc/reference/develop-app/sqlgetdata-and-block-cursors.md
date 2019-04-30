---
title: SQLGetData и блочные курсоры | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a14c98f045fd974b404209cc998496dc5fa7193e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149070"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData и блочные курсоры
**SQLGetData** работает по одному столбцу из одной строки и не может получить массив, содержащий данные из нескольких строк. Это так, как использовать основной **SQLGetData** — выборка данных long в части, и практически не причин для этого для более чем одной строке за раз.  
  
 Чтобы использовать **SQLGetData** с блочными, приложение сначала вызывает **SQLSetPos** для позиционирования курсора на одну строку. Затем он вызывает **SQLGetData** для столбца в этой строке. Однако такое поведение является необязательным. Чтобы определить, если драйвер поддерживает использование **SQLGetData** с блочными курсорами, приложение вызывает **SQLGetInfo** с параметром SQL_GETDATA_EXTENSIONS.
