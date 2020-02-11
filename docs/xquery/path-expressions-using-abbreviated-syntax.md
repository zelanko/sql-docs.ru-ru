---
title: Использование сокращенного синтаксиса в выражении пути | Документация Майкрософт
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
ms.openlocfilehash: 8e75db08f283631cf9b5daf064790786a1abc10f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946417"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>Выражения пути — использование сокращенного синтаксиса
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Во всех примерах, посвященных [выражениям пути в XQuery,](../xquery/path-expressions-xquery.md) для выражений пути используется несокращенный синтаксис. включающий в себя имя оси и элемент проверки узла, которые разделены двойным двоеточием, за которыми могут следовать квалификаторы шага.  
  
 Пример:  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 Запрос XQuery поддерживает в выражениях пути следующие сокращения.  
  
-   **Дочерняя** ось является осью по умолчанию. Поэтому дочернюю ось **::** Axis можно опустить из шага в выражении. Например, `/child::ProductDescription/child::Summary` может быть записано как `/ProductDescription/Summary`.  
  
-   Ось **атрибутов** можно сократить на @. Например, `/child::ProductDescription[attribute::ProductModelID=10]` может быть записано как `/ProudctDescription[@ProductModelID=10]`.  
  
-   **/Десцендант-ОР-Селф:: node ()/** может быть сокращен как//. Например, `/descendant-or-self::node()/child::act:telephoneNumber` может быть записано как `//act:telephoneNumber`.  
  
     Предыдущий запрос получает все телефонные номера, хранящиеся в столбце AdditionalContactInfo таблицы Contact. Схема для AdditionalContactInfo определяется таким образом, что элемент \<telephoneNumber> может располагаться в любом месте документа. Поэтому для получения всех телефонных номеров необходимо просмотреть каждый узел в документе. Поиск начинается от корня документа и проходит по всем узлам, являющимся его потомками.  
  
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
  
  
