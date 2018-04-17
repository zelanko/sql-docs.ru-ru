---
title: Закладки фиксированной длины | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 797a23c4fea5692cd01ce9fd05b56aeac27c3329
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если ODBC 3*.x* драйвер должен работать с ODBC 2. *x* , закладки использует фиксированной длины, драйвер должна поддерживать следующие приложения:  
  
-   SQL_UB_ON как значение параметра инструкции SQL_USE_BOOKMARKS. (В ODBC 3 устарел SQL_UB_ON*.x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
