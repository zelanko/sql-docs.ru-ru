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
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ccff64afd3a4df26b813bb30a84322d50519bd2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER таблицы
При dBASE или Paradox драйвер используется, когда индекс будет создана и добавлена запись новой, структура таблицы может быть изменен при выполнении инструкции ALTER TABLE, только индекс удаляется и содержимое таблицы удаляются.  
  
 Инструкции ALTER TABLE не поддерживаются для драйверов Microsoft Excel или текст.  
  
> [!NOTE]  
>  При использовании драйвера Paradox без реализации СУБД Borland инструкции ALTER TABLE не поддерживаются; только чтения и добавления инструкции являются допустимыми.
