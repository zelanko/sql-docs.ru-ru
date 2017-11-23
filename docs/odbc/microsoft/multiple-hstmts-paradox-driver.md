---
title: "Несколько hstmts (драйвер Paradox) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cfa1baa2b0744990f52562bf6e2c333590337b27
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="multiple-hstmts-paradox-driver"></a>Несколько hstmts (драйвер Paradox)
При использовании драйвера ODBC Paradox, если вы хотите использовать более одного *hstmt* для выполнения запросов в таблице, таблица должна иметь уникальный индекс (Paradox первичный ключ).
