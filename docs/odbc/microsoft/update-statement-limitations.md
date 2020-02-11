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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1cc8cf58d4e4d826dc4b152e395dedbea395a095
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088203"
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Чтобы драйвер Paradox имел возможность обновить таблицу, таблица должна иметь уникальный индекс (первичный ключ Paradox). При использовании драйвера Paradox без реализации ядро СУБД Borland обновление таблицы Paradox невозможно.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel можно обновить значения, но нельзя удалить строку из таблицы, основанной на электронной таблице Microsoft Excel. В результате инструкция UPDATE не считается официально поддерживаемой драйвером Microsoft Excel. Поддерживается только инструкция INSERT.
