---
description: Обновление, удаление или выборка по закладкам
title: Обновление, удаление или выборка по закладке | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2202e3483e13848ccac7f7e6f21145ba9704a8b7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448951"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Обновление, удаление или выборка по закладкам
Закладки можно использовать для обнаружения данных, которые должны быть обновлены в результирующем наборе, удалены из результирующего набора или получены из результирующего набора в буферы набора строк. Эти операции выполняются путем вызова **SQLBulkOperations** с аргументом *Option* SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK. Закладки, используемые в этих операциях, хранятся в столбце 0 буферов наборов строк. При обновлении с помощью закладки данные, обновляемые столбцами результирующего набора, извлекаются из буферов набора строк. Дополнительные сведения см. в разделе [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
