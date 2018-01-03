---
title: "Закладки фиксированной длины | Документы Microsoft"
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
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0b12009618489863c856d9b29433ff5146210ea
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если ODBC 3*.x* драйвер должен работать с ODBC 2. *x* , закладки использует фиксированной длины, драйвер должна поддерживать следующие приложения:  
  
-   SQL_UB_ON как значение параметра инструкции SQL_USE_BOOKMARKS. (В ODBC 3 устарел SQL_UB_ON*.x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
