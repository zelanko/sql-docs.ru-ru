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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088203"
---
# <a name="update-statement-limitations"></a>Ограничения инструкции UPDATE
Для обновления таблицы драйвера для Paradox таблица должна иметь уникальный индекс (первичный ключ для Paradox). При использовании драйвер для Paradox без реализации СУБД Borland, не может изменять таблицу Paradox.  
  
 Не поддерживается драйвером текста.  
  
 При использовании драйвера Microsoft Excel можно обновлять значения, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel. Таким образом инструкция UPDATE не является официально поддерживается драйвером Microsoft Excel. Только инструкция INSERT считается поддерживается.
