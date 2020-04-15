---
title: ОБНОВЛЕНИЕ, DELETE, и INSERT Заявления Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f12682a5d012d6981afce0085e9c920ed2f2ffbc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284264"
---
# <a name="update-delete-and-insert-statements"></a>Инструкции UPDATE, DELETE и INSERT
Приложения на основе S'L вносят изменения в таблицы, исполняя операторы **UPDATE,** **DELETE**и **INSERT.** Эти заявления являются частью минимального уровня соответствия грамматики S'L и должны быть поддержаны всеми драйверами и источниками данных.  
  
 Синтаксис этих утверждений:  
  
 **ОБНОВЛЕНИЕ** _название таблицы_  
  
 **SET** _столбец-идентификатор_ **=** -*выражение* &#124; **NULL**  
  
 - **=** **,** _столбец-идентификатор_ -*выражение* &#124; **NULL**  
  
 **Где** _поиск-условие_  
  
 **Удалить со** _стола-имя_-**где** _поиск-условие_  
  
 **INSERT INTO** _таблица-имя_- _(столбец-идентификатор_ **,** _столбец-идентификатор..._**(** **)**]  
  
 -*спецификация запроса* &#124; **VALUES** _(вставка-значение_ **,** _вставка-значение..._ **)**}  
  
 Обратите внимание, что элемент *спецификации запроса* действителен только в грамматике Core и Расширенной Грамматики S'L, а элементы *выражения* и *условия поиска* становятся более сложными в грамматике Core и Расширенной S'L.  
  
 Как и другие операторы S'L, **ОБНОВЛЕНИЕ**, **DELETE**, и **INSERT** заявления часто более эффективны, когда они используют параметры. Например, следующее утверждение может быть подготовлено и повторно выполнено для вставки нескольких строк в таблицу заказов:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Эта эффективность может быть увеличена путем прохождения массивов параметров значений. Для получения дополнительной [информации](../../../odbc/reference/develop-app/statement-parameters.md)о параметрах оператора и массивах значений параметров см.
