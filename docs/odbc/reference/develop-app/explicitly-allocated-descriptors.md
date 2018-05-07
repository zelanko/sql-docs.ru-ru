---
title: Явно выделенных дескрипторы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 7a9b34b2f83491c34d17f44da091dd7824bddb44
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенный дескрипторов
Приложение явно выделить дескриптор приложения для подключения в любое время, в которой он подключен к базе данных. Путем указания этого дескриптора как атрибут инструкции обрабатываются с помощью **SQLSetStmtAttr**, приложение направляет драйвер, который следует использовать вместо соответствующих этот дескриптор неявно выделена в приложение дескрипторы. Приложение нельзя указать альтернативные реализации дескрипторов.  
  
 Приложения можно поставить явно выделенный дескриптор более одной инструкции. Только в том случае, если приложение действительно подключен к базе данных дескриптор может быть явно выделенного дескриптора. Приложение можно освободить таких дескриптор явно или неявно, освобождая его подключения.
