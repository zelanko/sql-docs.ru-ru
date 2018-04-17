---
title: Ограничения обновления оператор | Документы Microsoft
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
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca36c4ae277aa36e9cbf2e4787b6131ce099ce17
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Для обновления таблицы драйвера Paradox таблица должна иметь уникальный индекс (Paradox первичный ключ). При использовании драйвера Paradox без реализации СУБД Borland не невозможно обновить таблицу Paradox.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel, можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel. В результате инструкция UPDATE не является официально поддерживается драйвером Microsoft Excel. Инструкции INSERT считается поддерживается.
