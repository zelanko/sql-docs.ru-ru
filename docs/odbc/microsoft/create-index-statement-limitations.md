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
manager: craigg
ms.openlocfilehash: ec6ba27197f7a6021aff90d30884129128cb3614
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837043"
---
# <a name="create-index-statement-limitations"></a>Ограничения инструкции CREATE INDEX
Инструкции CREATE INDEX не поддерживается для драйверов Microsoft Excel или текст.  
  
 Индекс можно определить более, чем 10 столбцов. Если более чем 10 столбцов включены в инструкцию CREATE INDEX, индекс не будет распознан, и таблицы будут рассматриваться, как если бы, если индекс не были созданы.  
  
 Драйвер для dBASE невозможно создать индекс по столбцу ЛОГИЧЕСКИХ.  
  
 Когда используется драйвер для dBASE, время ответа на больших файлов можно повысить, построение индекса .mdx (или .ndx) в столбце (поле), указанных в предложениях WHERE инструкции SELECT. Существующие индексы .mdx будут автоматически применяться для =, >, \<, > =, = < и МЕЖДУ операторами в предложении WHERE и предикатах LIKE, а также в предикатах соединения.  
  
 Если используется драйвер для dBASE, фактически неуникального индекса, созданного с помощью инструкции CREATE UNIQUE INDEX и повторяющиеся значения могут быть вставлены в индексированный столбец. Можно добавить только одну запись из набора с одинаковыми значениями ключа к индексу.  
  
 При использовании драйвер для Paradox при последовательных подмножества столбцов в таблице, включая первый столбец должен быть определен уникальный индекс. Невозможно изменить таблицу, драйвер для Paradox, если не определен уникальный индекс для таблицы или если драйвер для Paradox используется без реализации компонента Borland Database Engine.
