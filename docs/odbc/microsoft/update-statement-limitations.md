---
title: Ограничения обновления оператор | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 006d0f9644c9f62a6b50e2d327384ec3a9c954c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Для обновления таблицы драйвера Paradox таблица должна иметь уникальный индекс (Paradox первичный ключ). При использовании драйвера Paradox без реализации СУБД Borland не невозможно обновить таблицу Paradox.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel, можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel. В результате инструкция UPDATE не является официально поддерживается драйвером Microsoft Excel. Инструкции INSERT считается поддерживается.
