---
title: Закладки фиксированной длины | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
ms.openlocfilehash: b90454f8ecfa48081d17a71c63cc9f4ae670b4ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907829"
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если ODBC 3 *.x* драйвер должен работать с ODBC 2. *x* , закладки использует фиксированной длины, драйвер должна поддерживать следующие приложения:  
  
-   SQL_UB_ON как значение параметра инструкции SQL_USE_BOOKMARKS. (В ODBC 3 устарел SQL_UB_ON *.x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
