---
title: Обновление, удаление или выборка по закладкам | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5af3cad39739c3b85a0c6298d682d8e75a5918d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151225"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Обновление, удаление или выборка по закладкам
Закладки можно использовать для идентификации данные будут обновляться в результирующем наборе, удалены из результата задать или извлечь из результирующего набора в буферы строк. Эти операции выполняются с помощью вызова **SQLBulkOperations** с *параметр* аргумент SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK. Закладки, используемые в этих операциях хранятся в столбце 0 буферов набора строк. При обновлении по закладкам, данные, которые привести столбцы набора обновляются извлекается из буферов набора строк. Дополнительные сведения см. в разделе [обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
