---
title: "Извлечение закладки | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb71f5ce4b60a133d600367086cdf73c02a61461
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-bookmarks"></a>Извлечение закладки
Если приложение будет использовать закладки, его необходимо установить атрибут инструкции SQL_ATTR_USE_BOOKMARKS в SQL_UB_VARIABLE до подготовки или выполнения инструкции. Это необходимо, так как создавать и поддерживать закладки может быть дорогостоящей операцией, поэтому закладки должна быть включена только в том случае, если приложение может установить хороший используют их.  
  
 Закладки, возвращаются как столбец 0 результирующего набора. Приложение может получать их тремя способами:  
  
-   Привязать столбец 0 результирующего набора. **SQLFetch** или **SQLFetchScroll** возвращает закладки для каждой строки в наборе строк вместе с данными для других столбцы привязаны.  
  
-   Вызовите **SQLSetPos** для позиции строки в наборе строк, а затем вызвать **SQLGetData** для столбца с номером 0. Если драйвер поддерживает закладки, он всегда должен поддерживать возможность вызова **SQLGetData** для столбца 0, даже если он не позволяет приложениям вызывать **SQLGetData** для других столбцов перед последней привязки столбец.  
  
-   Вызовите **SQLBulkOperations** с *операции* SQL_ADD значением аргумента и связанный столбец 0. Курсор вставляет строку и возвращает закладка для строки в буфере связанный.
