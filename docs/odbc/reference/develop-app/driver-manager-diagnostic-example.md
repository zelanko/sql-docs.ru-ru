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
ms.openlocfilehash: 95392367b70af3eb820f0943af5dc668783a3fe5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046960"
---
# <a name="driver-manager-diagnostic-example"></a>Пример диагностики диспетчера драйверов
Диспетчер драйверов также может создавать диагностические сообщения. Например, если приложение передало недопустимый параметр Direction для **SQLDataSources**, диспетчер драйверов может отформатировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Поскольку ошибка произошла в диспетчере драйверов, она добавила префиксы в диагностическое сообщение для его поставщика ([Microsoft]) и его идентификатор ([Диспетчер драйверов ODBC]).
