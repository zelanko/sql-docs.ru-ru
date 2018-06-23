---
title: Создание областью действия сеанса вычисляемых элементов (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d8e51a2fa5d8179134ac2654f55e9da7ff5ced67
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096541"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a>Создание вычисляемых элементов с областью действия сеанса (многомерные выражения)
  Для создания вычисляемых элементов, доступных в сеансе многомерных выражений, используется инструкция [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member). Вычисляемый элемент, созданный с помощью инструкции CREATE MEMBER, удаляется только при закрытии сеанса многомерных выражений.  
  
 Как показано в этом разделе, синтаксис инструкции CREATE MEMBER достаточно прост.  
  
> [!NOTE]  
>  Дополнительные сведения о создании вычисляемых элементов см. в разделе [Создание вычисляемых элементов в многомерных выражениях (многомерные выражения)](mdx-calculated-members-building-calculated-members.md).  
  
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
 [Создание областью действия запроса вычисляемые элементы &#40;многомерных Выражений&#41;](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
