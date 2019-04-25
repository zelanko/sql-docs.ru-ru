---
title: UPDATE, DELETE и инструкций INSERT | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00732de7eca32dc8b2984fdda14163c77c66ad43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632482"
---
# <a name="update-delete-and-insert-statements"></a>Инструкции UPDATE, DELETE и INSERT
Приложения на основе SQL внесения изменений в таблицы, выполнив **обновление**, **удалить**, и **вставить** инструкций. Эти инструкции являются частью уровень соответствия SQL минимум грамматики и должны поддерживаться все драйверы и источники данных.  
  
 Используется следующий синтаксис этих операторов:  
  
 **ОБНОВЛЕНИЕ** _имя таблицы_  
  
 **SET** _column-identifier_ **=** {*expression* &#124; **NULL**}  
  
 [**,** _column-identifier_ **=** {*expression* &#124; **NULL**}]...  
  
 [**ГДЕ** _условие поиска_]  
  
 **УДАЛИТЬ из** _имя таблицы_[**ГДЕ** _условие поиска_]  
  
 **INSERT INTO** _имя таблицы_[**(** _идентификатор столбца_ [**,** _столбец идентификаторов_]... **)**]  
  
 {*query-specification* &#124; **VALUES (** _insert-value_ [**,** _insert-value_]...**)**}  
  
 Обратите внимание, что *спецификация запроса* элемент допустим только в основные и расширенные SQL грамматики и что *выражение* и *условие поиска* элементы становятся более Сложный тип в основные и расширенные SQL грамматики.  
  
 Другие инструкции SQL, такие как **обновление**, **удалить**, и **вставить** инструкций, обычно более эффективным, при использовании параметров. Например следующая инструкция можно подготовить и многократно выполняется, чтобы вставить несколько строк в таблице Orders:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Этой эффективности можно увеличить путем передачи массивы значений параметров. Дополнительные сведения о параметрах инструкции и массивы значений параметров см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
