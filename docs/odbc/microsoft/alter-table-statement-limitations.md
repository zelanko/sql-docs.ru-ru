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
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6c50ea6550e9dfb255c87886e4e0375240bcd2ae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER таблицы
При dBASE или Paradox драйвер используется, когда индекс будет создана и добавлена запись новой, структура таблицы может быть изменен при выполнении инструкции ALTER TABLE, только индекс удаляется и содержимое таблицы удаляются.  
  
 Инструкции ALTER TABLE не поддерживаются для драйверов Microsoft Excel или текст.  
  
> [!NOTE]  
>  При использовании драйвера Paradox без реализации СУБД Borland инструкции ALTER TABLE не поддерживаются; только чтения и добавления инструкции являются допустимыми.

