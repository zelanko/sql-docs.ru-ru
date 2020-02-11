---
title: Ограничения инструкции ALTER TABLE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1333cd6cd5946b7a3a70152e12f4d3decfa7fed0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138431"
---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER TABLE
Если используется драйвер dBASE или Paradox, то после создания индекса и добавления новой записи структура таблицы не может быть изменена инструкцией ALTER TABLE, если только индекс не будет удален и не будет удалено содержимое таблицы.  
  
 Инструкции ALTER TABLE не поддерживаются для Microsoft Excel или текстовых драйверов.  
  
> [!NOTE]  
>  При использовании драйвера Paradox без реализации ядро СУБД Borland инструкции ALTER TABLE не поддерживаются. допускаются только инструкции Read и Append.
