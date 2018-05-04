---
title: Явно выделенных дескрипторы | Документы Microsoft
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f09c3d7817fdb3d7f992255a7c2242c515e9748
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенный дескрипторов
Приложение явно выделить дескриптор приложения для подключения в любое время, в которой он подключен к базе данных. Путем указания этого дескриптора как атрибут инструкции обрабатываются с помощью **SQLSetStmtAttr**, приложение направляет драйвер, который следует использовать вместо соответствующих этот дескриптор неявно выделена в приложение дескрипторы. Приложение нельзя указать альтернативные реализации дескрипторов.  
  
 Приложения можно поставить явно выделенный дескриптор более одной инструкции. Только в том случае, если приложение действительно подключен к базе данных дескриптор может быть явно выделенного дескриптора. Приложение можно освободить таких дескриптор явно или неявно, освобождая его подключения.
