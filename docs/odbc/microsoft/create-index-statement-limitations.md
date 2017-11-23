---
title: "Создание ограничений инструкции ИНДЕКСА | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 38dfc79dcb6d12917368a3566522f7ff86edff66
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="create-index-statement-limitations"></a>Создание ограничений оператора ИНДЕКСА
Инструкции CREATE INDEX не поддерживается для драйверов Microsoft Excel или текст.  
  
 Индекс можно определить в более 10 столбцов. Если более чем 10 столбцов включаются в инструкции CREATE INDEX, не будут распознаны индекса и таблицы будут рассматриваться, как если бы, если индекс не были созданы.  
  
 Драйвер dBASE невозможно создать индекс для ЛОГИЧЕСКОГО столбца.  
  
 При использовании драйвера dBASE путем построения многомерных выражений (или .ndx) индекс на столбце (поле), указанных в предложениях WHERE инструкции SELECT можно улучшить время ответа на больших файлов. Существующие индексы многомерных выражений применяются автоматически для =, >, \<, > =, = <, а также МЕЖДУ операторами в предложении WHERE и предикатах LIKE, а также в предикатах соединения.  
  
 При использовании драйвера dBASE индекса, созданного с помощью инструкции CREATE UNIQUE INDEX фактически не являются уникальными и повторяющиеся значения могут быть вставлены в индексированный столбец. Только одна запись из набора с одинаковыми значениями ключа можно добавить в индекс.  
  
 При использовании драйвера Paradox после смежных подмножества столбцов в таблице, включая первый столбец должен быть определен уникальный индекс. Если не определен уникальный индекс для таблицы или при использовании драйвера Paradox без реализации компонента Borland Database Engine таблицу невозможно обновить драйвером Paradox.
