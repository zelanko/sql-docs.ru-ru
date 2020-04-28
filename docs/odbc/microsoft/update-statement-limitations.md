---
title: Ограничения инструкции UPDATE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ddf19c0b672901b2e778833f8bf624996d4ced3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307625"
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Чтобы драйвер Paradox имел возможность обновить таблицу, таблица должна иметь уникальный индекс (первичный ключ Paradox). При использовании драйвера Paradox без реализации ядро СУБД Borland обновление таблицы Paradox невозможно.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронной таблице Microsoft Excel. В результате инструкция UPDATE не считается официально поддерживаемой драйвером Microsoft Excel. Поддерживается только инструкция INSERT.
