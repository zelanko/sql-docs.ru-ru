---
title: "Ограничения обновления оператор | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 828fc042a4184bfedccf7c26210f899c1d73f2a4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Для обновления таблицы драйвера Paradox таблица должна иметь уникальный индекс (Paradox первичный ключ). При использовании драйвера Paradox без реализации СУБД Borland не невозможно обновить таблицу Paradox.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel, можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel. В результате инструкция UPDATE не является официально поддерживается драйвером Microsoft Excel. Инструкции INSERT считается поддерживается.

