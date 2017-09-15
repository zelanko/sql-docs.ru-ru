---
title: "Обновление, удаление или выборка по закладке | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07dacfde58f040c572a44c4f3ae15fe5d90a48cd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Обновление, удаление или выборка по закладке
Закладки можно использовать для определения данных для обновления в результирующем наборе, удалены из результата задать или извлечь из результирующего набора в буферы строк. Эти операции выполняются с помощью вызова **SQLBulkOperations** с *параметр* аргумент SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK. Закладки, используемые в этих операциях хранятся в столбце 0 буферов набора строк. При обновлении по закладке, привести столбцы набора данных обновляются извлекается из буферов набора строк. Дополнительные сведения см. в разделе [обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
