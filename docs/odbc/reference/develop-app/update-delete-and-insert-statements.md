---
title: Инструкции UPDATE, DELETE и INSERT | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284264"
---
# <a name="update-delete-and-insert-statements"></a>Инструкции UPDATE, DELETE и INSERT
Приложения на основе SQL делают изменения в таблицах, выполняя инструкции **Update**, **Delete**и **INSERT** . Эти инструкции являются частью минимального уровня соответствия грамматики SQL и должны поддерживаться всеми драйверами и источниками данных.  
  
 Синтаксис этих инструкций:  
  
 **Обновить** _таблицу-имя_  
  
 **Задать** _идентификатор_ **=** столбца {*выражение* &#124; **null**}  
  
 [**,** _столбец-Идентификатор_ **=** {*выражение* &#124; **null**}]...  
  
 [**Где** _Искать-условие_]  
  
 **Delete из** _таблицы-name_[**WHERE** _-условие поиска_]  
  
 **Вставить в** _таблицу с именем_[**(** _столбец-Идентификатор_ [**,** _столбец-Идентификатор_]... **)**]  
  
 {*Query-Specification* &#124; **значений (** _Вставка-значение_ [**,** _Вставка-значение_]... **)**}  
  
 Обратите внимание, что элемент *спецификации запроса* допустим только в основной и расширенной грамматике SQL, и элементы *выражения* и *условия поиска* становятся более сложными в ЯДРЕ и расширенной грамматике SQL.  
  
 Как и другие инструкции SQL, инструкции **Update**, **Delete**и **INSERT** часто более эффективны при использовании параметров. Например, следующая инструкция может быть подготовлена и многократно выполнена для вставки нескольких строк в таблицу Orders:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Эту эффективность можно увеличить, передав массивы значений параметров. Дополнительные сведения о параметрах инструкции и массивах значений параметров см. в разделе [Параметры инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
