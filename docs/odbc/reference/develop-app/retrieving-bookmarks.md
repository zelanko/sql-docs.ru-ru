---
title: Извлечение закладок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d7d4bd52a5f6e5b03a084cef4402e0a9044f97d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777632"
---
# <a name="retrieving-bookmarks"></a>Извлечение закладок
Если приложение будет использовать закладки, его необходимо задать атрибут инструкции SQL_ATTR_USE_BOOKMARKS для SQL_UB_VARIABLE до подготовки или выполнения инструкции. Это необходимо, так как создание и обслуживание закладки может быть ресурсоемкой операцией, закладки должно быть включено только в том случае, если можно строить приложения их использования.  
  
 Закладки, возвращаются как столбец 0 результирующего набора. Приложения их можно получить тремя способами:  
  
-   Привязать столбец 0 результирующего набора. **SQLFetch** или **SQLFetchScroll** возвращает закладки, для каждой строки в наборе строк, а также данные для других столбцы привязаны.  
  
-   Вызовите **SQLSetPos** для размещения в строку в наборе строк и затем вызвать **SQLGetData** для столбца 0. Если драйвер поддерживает закладки, он всегда должен поддерживать возможность вызова **SQLGetData** для столбца 0, даже если он не позволяет приложениям вызывать **SQLGetData** для других столбцов перед последней привязки столбец.  
  
-   Вызовите **SQLBulkOperations** с *операции* аргумента значение SQL_ADD и привязать столбец 0. Курсор вставляет строку и возвращает закладка для строки в буфере привязки.
