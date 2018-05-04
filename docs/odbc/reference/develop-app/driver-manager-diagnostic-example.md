---
title: Пример Диагностика диспетчера драйверов | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b5abbaad714c483a67bd4e3de547449ef358e68
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="driver-manager-diagnostic-example"></a>Пример Диагностика диспетчера драйверов
Диспетчер драйверов можно также создавать соответствующие диагностические сообщения. Например, если приложение передано неверное направление возможность **SQLDataSources**, диспетчер драйверов может форматировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Из-за ошибки диспетчера драйверов, он добавляется префиксы диагностическое сообщение для его поставщика ([Microsoft]) и его идентификатору ([Диспетчер драйверов ODBC]).
