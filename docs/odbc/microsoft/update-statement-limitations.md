---
title: "Ограничения обновления оператор | Документы Microsoft"
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
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 502315916781ae5624f94e099c0cd95c52ffe8a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Для обновления таблицы драйвера Paradox таблица должна иметь уникальный индекс (Paradox первичный ключ). При использовании драйвера Paradox без реализации СУБД Borland не невозможно обновить таблицу Paradox.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel, можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel. В результате инструкция UPDATE не является официально поддерживается драйвером Microsoft Excel. Инструкции INSERT считается поддерживается.
