---
title: Архитектуры доступа к стандартной базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ff5ee3c22a01b0b1963f1ca6021e72502aa377b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724122"
---
# <a name="standard-database-access-architectures"></a>Стандартные архитектуры доступа к базе данных
Изучить компоненты доступа базы данных, описанные в предыдущем разделе, оказывается, что два из них — программирования интерфейсы и данные, потоковую передачу протоколов – являются хорошими кандидатами для стандартизации. Эти два компонента — IPC механизм и сетевые протоколы, не только находятся слишком низкого уровня, но оба сильно зависит от сети и операционной системы. Имеется также третий подход — шлюзов, который предоставляет возможности для стандартизации.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Стандартный интерфейс программирования](../../odbc/reference/standard-programming-interface.md)  
  
-   [Стандартный протокол потока данных](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Стандартный шлюз](../../odbc/reference/standard-gateway.md)
