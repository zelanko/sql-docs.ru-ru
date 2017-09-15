---
title: "Пример Диагностика диспетчера драйверов | Документы Microsoft"
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
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3f373fe012c2b791329fea35ca853021e70274eb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="driver-manager-diagnostic-example"></a>Пример Диагностика диспетчера драйверов
Диспетчер драйверов можно также создавать соответствующие диагностические сообщения. Например, если приложение передано неверное направление возможность **SQLDataSources**, диспетчер драйверов может форматировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Из-за ошибки диспетчера драйверов, он добавляется префиксы диагностическое сообщение для его поставщика ([Microsoft]) и его идентификатору ([Диспетчер драйверов ODBC]).
