---
description: Ограничения инструкции CREATE INDEX
title: Ограничения инструкции CREATE INDEX | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db2b346afa13e7f7f37151d6d4fa8efdca9fa230
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466456"
---
# <a name="create-index-statement-limitations"></a>Ограничения инструкции CREATE INDEX
Инструкция CREATE INDEX не поддерживается для Microsoft Excel или текстовых драйверов.  
  
 Индекс может быть определен не более чем в 10 столбцах. Если в инструкцию CREATE INDEX включены более 10 столбцов, индекс не будет распознан, а таблица будет обрабатываться так, как будто индекс не был создан.  
  
 Драйверу dBASE не удается создать индекс для логического столбца.  
  
 При использовании драйвера dBASE время отклика на большие файлы можно улучшить, создав индекс многомерных выражений (или ндкс) в столбце (поле), указанном в предложениях WHERE инструкции SELECT. Существующие индексы многомерных выражений будут автоматически применены к операторам =, >, \<, > =, =< и between в предложении WHERE, а также в предикатах JOIN.  
  
 При использовании драйвера dBASE индекс, созданный инструкцией CREATE UNIQUE INDEX, фактически не уникален, а повторяющиеся значения могут быть вставлены в индексированный столбец. В индекс можно добавить только одну запись из набора с идентичными значениями ключа.  
  
 При использовании драйвера Paradox необходимо определить уникальный индекс для непрерывного подмножества столбцов в таблице, включая первый столбец. Таблица не может быть обновлена драйвером Paradox, если в таблице не определен уникальный индекс или если драйвер Paradox используется без реализации ядро СУБД Borland.
