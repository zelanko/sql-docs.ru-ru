---
title: CREATE INDEX Заявление Ограничения (ru) Документы Майкрософт
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
ms.openlocfilehash: 053287d5087b377429221c31dd4e6b20f24248e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280885"
---
# <a name="create-index-statement-limitations"></a>Ограничения инструкции CREATE INDEX
Заявление CREATE INDEX не поддерживается для драйверов Microsoft Excel или Text.  
  
 Индекс может быть определен максимум на 10 столбцах. Если в выписку CREATE INDEX включено более 10 столбцов, индекс не будет распознан, а таблица будет рассматриваться как нерабочий индекс.  
  
 Драйвер dBASE не может создать индекс на столбце LOGICAL.  
  
 При использовании драйвера dBASE время отклика на больших файлах может быть улучшено путем создания индекса .mdx (или .ndx) на столбце (поле), указанном в положениях WHERE оператора SELECT. Существующие индексы .mdx будут автоматически применяться для операторов q, >, \<>,< и BETWEEN в оговорке WHERE и LIKE, а также в предикатах соединения.  
  
 При использовании драйвера dBASE индекс, созданный заявлением CREATE UNIQUE INDEX, на самом деле не является уникальным, и дублирующие значения могут быть вставлены в индексированный столбец. К индексу может быть добавлена только одна запись из набора с одинаковыми значениями ключевых клавиш.  
  
 При использовании драйвера Парадокса необходимо определить уникальный индекс на смежном подмножестве столбцов в таблице, включая первую колонку. Таблица не может быть обновлена драйвером Paradox, если уникальный индекс не определен на столе или когда драйвер Парадокса используется без реализации двигателя базы данных Borland.
