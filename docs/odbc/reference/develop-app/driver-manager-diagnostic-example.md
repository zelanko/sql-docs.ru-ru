---
title: Пример диагностики диспетчера драйверов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ad253c2d0603846d6d1f795f6115e7bb727b3da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778592"
---
# <a name="driver-manager-diagnostic-example"></a>Пример диагностики диспетчера драйверов
Диспетчер драйверов можно также создавать соответствующие диагностические сообщения. Например, если приложение передано неверное направление возможность **SQLDataSources**, диспетчер драйверов может форматировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Из-за ошибки в диспетчере драйверов, она добавляется префиксы диагностическое сообщение для его поставщика ([Microsoft]) и его идентификатору ([Диспетчер драйверов ODBC]).
