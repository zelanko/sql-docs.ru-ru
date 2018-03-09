---
title: "Типы изменений | Документы Microsoft"
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
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7801d7bf8e7add5425ee6a8a97c4b1b17c556674
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-changes"></a>Типы изменений
Трех типов изменений внесенных в ODBC 3. *x* (и любой версии ODBC). Каждый из них по-разному влияет на обратной совместимости и обрабатываются по-разному. Эти изменения описаны в следующей таблице.  
  
|Тип изменения|Description|  
|--------------------|-----------------|  
|Новые возможности|Это функции, которые появились в ODBC 3. *x*, такие как привязка вне строки или дескрипторов. Они реализованы только в том случае, если приложение драйвера, а также диспетчера драйверов, имеют версии 3*.x*, поэтому не выполняется, чтобы сделать эти обратной совместимости.|  
|Повторяющийся функции|Это функции, которые существуют в ODBC 2*.x* а ODBC 3. *x* реализуется по-разному в каждой. Функции **SQLAllocHandle** и **SQLAllocStmt** приведен пример. Обратная совместимость выдает эти и другие повторяющиеся функции, главным образом обрабатываются сопоставления диспетчера драйверов.|  
|Изменения поведения|Это функции, которые обрабатываются по-разному в ODBC 2*.x* а ODBC 3. *x*. Значения даты и времени **#define** приведен пример. Эти возможности обеспечиваются службами ODBC 3. *x* драйвер на основании атрибута параметры среды. (См. [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md) подробнее.)|
