---
title: "Ограничения инструкции ALTER таблицы | Документы Microsoft"
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
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: acdeccfa07141c267a77a927217ad2ec610034c7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER таблицы
При dBASE или Paradox драйвер используется, когда индекс будет создана и добавлена запись новой, структура таблицы может быть изменен при выполнении инструкции ALTER TABLE, только индекс удаляется и содержимое таблицы удаляются.  
  
 Инструкции ALTER TABLE не поддерживаются для драйверов Microsoft Excel или текст.  
  
> [!NOTE]  
>  При использовании драйвера Paradox без реализации СУБД Borland инструкции ALTER TABLE не поддерживаются; только чтения и добавления инструкции являются допустимыми.
