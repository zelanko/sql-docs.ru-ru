---
title: "Дескрипторы среды | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3f9f6ce261a111df12a12f0a6566e8b4fccabc2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="environment-handles"></a>Дескрипторы среды
*Среды* является глобальный контекст, в котором для доступа к данным, а связанные со средой — все сведения, который является глобальным по своей природе, такие как:  
  
-   Состояния среды  
  
-   Текущий уровень среды диагностики  
  
-   Дескрипторы соединений, выделенные в данный момент в среде  
  
-   Текущие параметры всех атрибутов среды  
  
 В это часть кода, который реализует ODBC (диспетчера драйверов или драйвер) дескриптор среды определяет структуры, содержащие эти сведения.  
  
 Дескрипторы среды не часто используются в приложениях ODBC. Всегда используются в вызовах **SQLDataSources** и **SQLDrivers** и иногда используется для вызова **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, и **SQLGetDiagRec**.  
  
 Каждый фрагмент кода, реализующего ODBC (диспетчера драйверов или драйвер) содержит один или несколько дескрипторов среды. Например диспетчер драйверов сохраняются дескриптор отдельную среду для каждого приложения, подключенные к нему. Дескрипторы среды выделяются с **SQLAllocHandle** и освобождается с помощью **SQLFreeHandle**.
