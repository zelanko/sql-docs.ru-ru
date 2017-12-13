---
title: "Создание областью действия сеанса с именем наборами (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b3970440812f0866d08e99bb195308a1780afbc6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-named-sets---creating-session-scoped-named-sets"></a>Именованные наборы - Создание областью действия сеанса многомерных Выражений именованных наборов
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Чтобы создать именованный набор, доступных в сеансе многомерных выражений (MDX), используйте [CREATE SET](../../../mdx/mdx-data-definition-create-set.md) инструкции. Именованный набор, созданный с помощью инструкции CREATE SET, удаляется только при закрытии сеанса многомерных выражений.  
  
 Синтаксис ключевого слова WITH достаточно прост.  
  
> [!NOTE]  
>  Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md).  
  
## <a name="create-set-syntax"></a>Синтаксис инструкции CREATE SET  
 При обращении к инструкции CREATE SET используется следующий синтаксис.  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 В синтаксисе инструкции CREATE SET параметр `cube name` представляет собой имя куба, содержащего элементы именованного набора. Если параметр `cube name` не указан, то в качестве куба, содержащего элементы именованного набора, используется текущий куб. Кроме того, параметр `Set_Identifier` содержит псевдоним именованного набора, а параметр `Set_Expression` — выражение набора, на который будет ссылаться заданный псевдоним именованного набора.  
  
## <a name="create-set-example"></a>Пример инструкции CREATE SET  
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
  
## <a name="see-also"></a>См. также  
 [Создание именованных наборов с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
