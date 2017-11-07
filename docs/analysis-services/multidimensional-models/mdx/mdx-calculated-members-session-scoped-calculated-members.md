---
title: "Создание областью действия сеанса вычисляемых элементов (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5da8ae05dc547de946228bb371df0b98a724ce41
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-calculated-members---session-scoped-calculated-members"></a>Многомерные Выражения вычисляемых элементов - вычисляемых элементов с областью действия сеанса
  Для создания вычисляемых элементов, доступных в сеансе многомерных выражений, используется инструкция [CREATE MEMBER](../../../mdx/mdx-data-definition-create-member.md) . Вычисляемый элемент, созданный с помощью инструкции CREATE MEMBER, удаляется только при закрытии сеанса многомерных выражений.  
  
 Как показано в этом разделе, синтаксис инструкции CREATE MEMBER достаточно прост.  
  
> [!NOTE]  
>  Дополнительные сведения о создании вычисляемых элементов см. в разделе [Создание вычисляемых элементов в многомерных выражениях (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="create-member-syntax"></a>Синтаксис инструкции CREATE MEMBER  
 Чтобы включить инструкцию CREATE MEMBER в инструкцию многомерных выражений, используйте следующее синтаксическое выражение:  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 В инструкции CREATE MEMBER аргумент `fully-qualified-member-name` — это полное имя вычисляемого элемента. Полное имя включает в себя измерение или уровень, с которым связан вычисляемый элемент. Аргумент `expression` возвращает значение вычисляемого элемента после определения значения выражения.  
  
## <a name="create-member-example"></a>Пример инструкции CREATE MEMBER  
 В следующем примере вычисляемый элемент `LastFourStores` создается с помощью инструкции CREATE MEMBER. Этот вычисляемый элемент возвращает количество товара, проданного четырьмя последними магазинами. Он доступен в течение всего сеанса куба.  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a>См. также  
 [Создание вычисляемых элементов с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md)  
  
  

