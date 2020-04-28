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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 839095e5544cab73cdddd4f4b17a3d8d52136c9c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305815"
---
# <a name="driver-manager-diagnostic-example"></a>Пример диагностики диспетчера драйверов
Диспетчер драйверов также может создавать диагностические сообщения. Например, если приложение передало недопустимый параметр Direction для **SQLDataSources**, диспетчер драйверов может отформатировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Поскольку ошибка произошла в диспетчере драйверов, она добавила префиксы в диагностическое сообщение для его поставщика ([Microsoft]) и его идентификатор ([Диспетчер драйверов ODBC]).
