---
title: ОБНОВЛЕНИЕ Заявление Ограничения (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307625"
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Для того чтобы драйвер Парадоксобновляя обновили таблицу, таблица должна иметь уникальный индекс (основной ключ Парадокса). При использовании драйвера Paradox без реализации системы базы данных Borland невозможно обновить таблицу Paradox.  
  
 Не поддерживается драйвером Текста.  
  
 При использовании драйвера Microsoft Excel можно обновить значения, но строка не может быть удалена из таблицы на основе электронной таблицы Microsoft Excel. В результате заявление UPDATE не считается официально поддержанным драйвером Microsoft Excel. Поддерживается только заявление INSERT.
