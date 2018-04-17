---
title: Ограничения инструкции ALTER таблицы | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06af545611da90d51ad0fc82136a4cb1ecc3984c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER таблицы
При dBASE или Paradox драйвер используется, когда индекс будет создана и добавлена запись новой, структура таблицы может быть изменен при выполнении инструкции ALTER TABLE, только индекс удаляется и содержимое таблицы удаляются.  
  
 Инструкции ALTER TABLE не поддерживаются для драйверов Microsoft Excel или текст.  
  
> [!NOTE]  
>  При использовании драйвера Paradox без реализации СУБД Borland инструкции ALTER TABLE не поддерживаются; только чтения и добавления инструкции являются допустимыми.
