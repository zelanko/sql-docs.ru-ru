---
title: Несколько hstmts (драйвер Paradox) | Документы Microsoft
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
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8306e830837049797c69ad3ea5241162948c243f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="multiple-hstmts-paradox-driver"></a>Несколько hstmts (драйвер Paradox)
При использовании драйвера ODBC Paradox, если вы хотите использовать более одного *hstmt* для выполнения запросов в таблице, таблица должна иметь уникальный индекс (Paradox первичный ключ).
