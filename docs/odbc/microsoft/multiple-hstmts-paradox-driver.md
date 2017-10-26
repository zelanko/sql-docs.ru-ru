---
title: "Несколько hstmts (драйвер Paradox) | Документы Microsoft"
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
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8720a5f196b9e7d2beddc2de2780ce5598c3dc35
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="multiple-hstmts-paradox-driver"></a>Несколько hstmts (драйвер Paradox)
При использовании драйвера ODBC Paradox, если вы хотите использовать более одного *hstmt* для выполнения запросов в таблице, таблица должна иметь уникальный индекс (Paradox первичный ключ).

