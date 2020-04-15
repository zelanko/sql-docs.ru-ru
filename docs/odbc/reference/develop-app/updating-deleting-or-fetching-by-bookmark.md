---
title: Обновление, утилизирование или извлечение по закладке Документы Майкрософт
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
ms.openlocfilehash: 5e94a98bb577ef906afbb04539761fd07d15f772
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286154"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Обновление, удаление или выборка по закладкам
Закладки могут использоваться для идентификации данных, которые должны обновляться в наборе результатов, удаляться из набора результатов или получать из набора результатов в буферы набора строк. Эти операции выполняются путем вызова в **S'LBulkOperations** с аргументом *опции* SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK. Закладки, используемые в этих операциях, хранятся в столбце 0 буферов рядов. При обновлении закладкой данные, которые приводят к набору столбцов, обновляются, извлекаются из буферов набора строк. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)
