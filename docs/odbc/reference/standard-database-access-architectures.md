---
title: "Архитектуры доступа к стандартной базы данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff9ebb61d8a0446f4c6015dd5c0ae56c22ebfc45
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="standard-database-access-architectures"></a>Архитектуры доступа к стандартной базы данных
Анализ компонентов доступа базы данных, описанные в предыдущем разделе, оказывается, два из них — программный интерфейс и данные потока протоколы — хорошо подходят для стандартизации. Эти два компонента — IPC механизм и сетевые протоколы, не только находятся на слишком низкого уровня, но оба сильно зависит от сети и операционной системы. Имеется также третий подход — шлюзы —, предоставляющий возможности для стандартизации.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Стандартный интерфейс программирования](../../odbc/reference/standard-programming-interface.md)  
  
-   [Стандартные данные потока протокола](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Стандартный шлюз](../../odbc/reference/standard-gateway.md)
