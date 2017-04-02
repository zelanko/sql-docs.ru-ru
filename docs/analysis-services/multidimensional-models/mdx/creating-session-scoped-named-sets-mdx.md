---
title: "Создание именованных наборов с областью действия сеанса (многомерные выражения) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CREATE SET, инструкция"
  - "именованные наборы с областью действия сеанса [многомерные выражения]"
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Создание именованных наборов с областью действия сеанса (многомерные выражения)
  Для создания именованного набора, доступного в сеансе многомерных выражений, используется инструкция [CREATE SET](../Topic/CREATE%20SET%20Statement%20\(MDX\).md). Именованный набор, созданный с помощью инструкции CREATE SET, удаляется только при закрытии сеанса многомерных выражений.  
  
 Синтаксис ключевого слова WITH достаточно прост.  
  
> [!NOTE]  
>  Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](../../../analysis-services/multidimensional-models/mdx/building-named-sets-in-mdx-mdx.md).  
  
## Синтаксис инструкции CREATE SET  
 При обращении к инструкции CREATE SET используется следующий синтаксис.  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 В синтаксисе инструкции CREATE SET параметр `cube name` представляет собой имя куба, содержащего элементы именованного набора. Если параметр `cube name` не указан, то в качестве куба, содержащего элементы именованного набора, используется текущий куб. Кроме того, параметр `Set_Identifier` содержит псевдоним именованного набора, а параметр `Set_Expression` — выражение набора, на который будет ссылаться заданный псевдоним именованного набора.  
  
## Пример инструкции CREATE SET  
 В следующем примере иллюстрируется использование инструкции CREATE SET для создания именованного набора `SetCities_2_3` на основе куба Store. Элементы именованного набора `SetCities_2_3` — это магазины в городе 2 и городе 3.  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 При создании именованного набора `SetCities_2_3` с помощью инструкции CREATE SET он остается доступным в течение текущего сеанса многомерных выражений. Следующий пример — это допустимый запрос, возвращающий элементы городов 2 и 3. Его можно выполнять в любой момент после создания именованного набора `SetCities_2_3` до завершения сеанса.  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## См. также  
 [Создание именованных наборов с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-named-sets-mdx.md)  
  
  