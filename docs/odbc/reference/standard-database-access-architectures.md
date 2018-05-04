---
title: Архитектуры доступа к стандартной базы данных | Документы Microsoft
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
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99e0a0eee2636a04d182076bb580b1ccf8069921
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="standard-database-access-architectures"></a>Архитектуры доступа к стандартной базы данных
Анализ компонентов доступа базы данных, описанные в предыдущем разделе, оказывается, два из них — программный интерфейс и данные потока протоколы — хорошо подходят для стандартизации. Эти два компонента — IPC механизм и сетевые протоколы, не только находятся на слишком низкого уровня, но оба сильно зависит от сети и операционной системы. Имеется также третий подход — шлюзы —, предоставляющий возможности для стандартизации.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Стандартный интерфейс программирования](../../odbc/reference/standard-programming-interface.md)  
  
-   [Стандартный протокол потока данных](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Стандартный шлюз](../../odbc/reference/standard-gateway.md)
