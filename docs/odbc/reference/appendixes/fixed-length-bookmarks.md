---
title: "Закладки фиксированной длины | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
ms.openlocfilehash: 20f9d91887f020cd6753ed8be684e5caa32ba99c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если ODBC 3*.x* драйвер должен работать с ODBC 2. *x* , закладки использует фиксированной длины, драйвер должна поддерживать следующие приложения:  
  
-   SQL_UB_ON как значение параметра инструкции SQL_USE_BOOKMARKS. (В ODBC 3 устарел SQL_UB_ON*.x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
