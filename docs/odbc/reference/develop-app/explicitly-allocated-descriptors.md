---
title: "Явно выделенных дескрипторы | Документы Microsoft"
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a4679fa6c6d2185f6e474407882080fea6b7c8a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенный дескрипторов
Приложение явно выделить дескриптор приложения для подключения в любое время, в которой он подключен к базе данных. Путем указания этого дескриптора как атрибут инструкции обрабатываются с помощью **SQLSetStmtAttr**, приложение направляет драйвер, который следует использовать вместо соответствующих этот дескриптор неявно выделена в приложение дескрипторы. Приложение нельзя указать альтернативные реализации дескрипторов.  
  
 Приложения можно поставить явно выделенный дескриптор более одной инструкции. Только в том случае, если приложение действительно подключен к базе данных дескриптор может быть явно выделенного дескриптора. Приложение можно освободить таких дескриптор явно или неявно, освобождая его подключения.

