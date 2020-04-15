---
title: Драйвер менеджер Диагностический Пример (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305815"
---
# <a name="driver-manager-diagnostic-example"></a>Пример диагностики диспетчера драйверов
Менеджер драйвера также может генерировать диагностические сообщения. Например, если приложение передало недействительную опцию направления в **S'LDataSources,** менеджер драйверов может форматировать и вернуть следующие значения из **S'LGetDiagRec:**  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Поскольку ошибка произошла в менеджере драйвера, он добавил префиксы к диагностическому сообщению для своего поставщика («Microsoft») и его идентификатору («менеджер драйверов ODBC»).
