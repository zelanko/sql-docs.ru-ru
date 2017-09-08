---
title: "С помощью сокращенный синтаксис в выражении пути | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cd4ed101bc96fb8c5c417ec1c47063d747af29df
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="path-expressions---using-abbreviated-syntax"></a>Выражения пути — использование сокращенного синтаксиса
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Все примеры в [основные сведения о выражениях пути в XQuery](../xquery/path-expressions-xquery.md) для выражений пути используется полный синтаксис. включающий в себя имя оси и элемент проверки узла, которые разделены двойным двоеточием, за которыми могут следовать квалификаторы шага.  
  
 Например:  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 Запрос XQuery поддерживает в выражениях пути следующие сокращения.  
  
-   **Дочерних** ось — по умолчанию. Таким образом **дочерних::** оси можно исключить из шага в выражении. Например, `/child::ProductDescription/child::Summary` может быть записано как `/ProductDescription/Summary`.  
  
-   **Атрибута** оси можно использовать сокращение @. Например, `/child::ProductDescription[attribute::ProductModelID=10]` может быть записано как `/ProudctDescription[@ProductModelID=10]`.  
  
-   Объект **/descendant-or-self::node()/** может использоваться сокращение / /. Например, `/descendant-or-self::node()/child::act:telephoneNumber` может быть записано как `//act:telephoneNumber`.  
  
     Предыдущий запрос получает все телефонные номера, хранящиеся в столбце AdditionalContactInfo таблицы Contact. Схема для столбца AdditionalContactInfo определена таким образом, \<telephoneNumber > элемент может находиться в любом месте документа. Поэтому для получения всех телефонных номеров необходимо просмотреть каждый узел в документе. Поиск начинается от корня документа и проходит по всем узлам, являющимся его потомками.  
  
     Следующий запрос получает все контактные телефонные номера для указанного клиента:  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="http://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     Если выражение пути заменяется сокращенным синтаксическим выражением, `//act:telephoneNumber` обеспечивает тот же самый результат.  
  
-   **Self:: node()** на шаге можно сократить до одной точки (.). Однако точка не является эквивалентным или взаимозаменяемым с **self:: node()**.  
  
     Например, в следующем запросе точка представляет значение, а не узел:  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   **Parent:: node()** в шаге может быть заменен двумя точками (.).  
  
  
