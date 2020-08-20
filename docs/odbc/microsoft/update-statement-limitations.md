---
description: Ограничения инструкции UPDATE
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
ms.openlocfilehash: b7c1ea2e5e9d887005084cdb5454dcf9b5e8fa24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471403"
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Чтобы драйвер Paradox имел возможность обновить таблицу, таблица должна иметь уникальный индекс (первичный ключ Paradox). При использовании драйвера Paradox без реализации ядро СУБД Borland обновление таблицы Paradox невозможно.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронной таблице Microsoft Excel. В результате инструкция UPDATE не считается официально поддерживаемой драйвером Microsoft Excel. Поддерживается только инструкция INSERT.
