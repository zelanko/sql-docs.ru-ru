---
title: Закладки фиксированной длины | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5877a6cb7a99803f854338321e333c87037c2e90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913587"
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если ODBC *3.x* драйвер должны работать с ODBC *2.x* приложения, что закладки фиксированной длины использует, драйвер должен поддерживать следующее:  
  
-   SQL_UB_ON как значение для параметра инструкции SQL_USE_BOOKMARKS. (SQL_UB_ON является устаревшей в ODBC *3.x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
