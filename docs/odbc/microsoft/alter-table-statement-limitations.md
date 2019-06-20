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
manager: craigg
ms.openlocfilehash: 02ce530385cdc911250a81d831dd2fdb81873f76
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63301979"
---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER TABLE
Когда dBASE или драйвер для Paradox используется, после создания индекса и добавления новой записи, структура таблицы может быть изменен с помощью инструкции ALTER TABLE, только индекс удаляется и содержание таблицы удаляются.  
  
 Инструкции ALTER TABLE не поддерживаются для драйверов Microsoft Excel или текст.  
  
> [!NOTE]  
>  При использовании драйвер для Paradox без реализации СУБД Borland, инструкции ALTER TABLE не поддерживаются; только чтения и добавления инструкции являются допустимыми.
