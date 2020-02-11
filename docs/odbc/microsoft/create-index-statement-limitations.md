---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ddb695d996cdd40b7fde4087799e5c1ec84224c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081931"
---
# <a name="create-index-statement-limitations"></a>Ограничения инструкции CREATE INDEX
Инструкция CREATE INDEX не поддерживается для Microsoft Excel или текстовых драйверов.  
  
 Индекс может быть определен не более чем в 10 столбцах. Если в инструкцию CREATE INDEX включены более 10 столбцов, индекс не будет распознан, а таблица будет обрабатываться так, как будто индекс не был создан.  
  
 Драйверу dBASE не удается создать индекс для логического столбца.  
  
 При использовании драйвера dBASE время отклика на большие файлы можно улучшить, создав индекс многомерных выражений (или ндкс) в столбце (поле), указанном в предложениях WHERE инструкции SELECT. Существующие многомерные выражения будут автоматически применены для =, >, \<, >=, =< и между операторами в предложении WHERE, а также в предикатах JOIN.  
  
 При использовании драйвера dBASE индекс, созданный инструкцией CREATE UNIQUE INDEX, фактически не уникален, а повторяющиеся значения могут быть вставлены в индексированный столбец. В индекс можно добавить только одну запись из набора с идентичными значениями ключа.  
  
 При использовании драйвера Paradox необходимо определить уникальный индекс для непрерывного подмножества столбцов в таблице, включая первый столбец. Таблица не может быть обновлена драйвером Paradox, если в таблице не определен уникальный индекс или если драйвер Paradox используется без реализации ядро СУБД Borland.
