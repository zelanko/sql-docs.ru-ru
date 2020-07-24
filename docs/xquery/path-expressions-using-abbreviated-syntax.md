---
title: Использование сокращенного синтаксиса в выражении пути | Документация Майкрософт
description: Узнайте, как использовать сокращенный синтаксис в выражениях пути XQuery.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b8270babb8fe592c050a9352a7fd687660b178e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920100"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>Выражения пути — использование сокращенного синтаксиса
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

  Во всех примерах, посвященных [выражениям пути в XQuery,](../xquery/path-expressions-xquery.md) для выражений пути используется несокращенный синтаксис. включающий в себя имя оси и элемент проверки узла, которые разделены двойным двоеточием, за которыми могут следовать квалификаторы шага.  
  
 Например.  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 Запрос XQuery поддерживает в выражениях пути следующие сокращения.  
  
-   **Дочерняя** ось является осью по умолчанию. Поэтому дочернюю ось **::** Axis можно опустить из шага в выражении. Например, `/child::ProductDescription/child::Summary` может быть записано как `/ProductDescription/Summary`.  
  
-   Ось **атрибутов** можно сократить на @ . Например, `/child::ProductDescription[attribute::ProductModelID=10]` может быть записано как `/ProudctDescription[@ProductModelID=10]`.  
  
-   **/Десцендант-ОР-Селф:: node ()/** может быть сокращен как//. Например, `/descendant-or-self::node()/child::act:telephoneNumber` может быть записано как `//act:telephoneNumber`.  
  
     Предыдущий запрос получает все телефонные номера, хранящиеся в столбце AdditionalContactInfo таблицы Contact. Схема для AdditionalContactInfo определяется таким образом, что \<telephoneNumber> элемент может располагаться в любом месте документа. Поэтому для получения всех телефонных номеров необходимо просмотреть каждый узел в документе. Поиск начинается от корня документа и проходит по всем узлам, являющимся его потомками.  
  
     Следующий запрос получает все контактные телефонные номера для указанного клиента:  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="https://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     Если выражение пути заменяется сокращенным синтаксическим выражением, `//act:telephoneNumber` обеспечивает тот же самый результат.  
  
-   **Self:: node ()** в шаге можно сократить до одной точки (.). Однако точка не эквивалентна или взаимозаменяема с **Self:: node ()**.  
  
     Например, в следующем запросе точка представляет значение, а не узел:  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   **Родительский элемент:: node ()** в шаге можно сократить до двойной точки (..).  
  
  
