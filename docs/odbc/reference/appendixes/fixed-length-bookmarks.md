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
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 279b6a3c1f8eb2f1eea5bba35ee10f0a6643fb49
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если ODBC 3*.x* драйвер должен работать с ODBC 2. *x* , закладки использует фиксированной длины, драйвер должна поддерживать следующие приложения:  
  
-   SQL_UB_ON как значение параметра инструкции SQL_USE_BOOKMARKS. (В ODBC 3 устарел SQL_UB_ON*.x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.

