---
title: "Явно выделенных дескрипторы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 791d7620afc4f952ccb99c80cad980ebd2e2e9ea
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенный дескрипторов
Приложение явно выделить дескриптор приложения для подключения в любое время, в которой он подключен к базе данных. Путем указания этого дескриптора как атрибут инструкции обрабатываются с помощью **SQLSetStmtAttr**, приложение направляет драйвер, который следует использовать вместо соответствующих этот дескриптор неявно выделена в приложение дескрипторы. Приложение нельзя указать альтернативные реализации дескрипторов.  
  
 Приложения можно поставить явно выделенный дескриптор более одной инструкции. Только в том случае, если приложение действительно подключен к базе данных дескриптор может быть явно выделенного дескриптора. Приложение можно освободить таких дескриптор явно или неявно, освобождая его подключения.
