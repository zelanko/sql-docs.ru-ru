---
title: Создание областью действия сеанса с именем наборами (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fdf177cedcd73069e73c1ec7b4c7db5cfb497969
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-named-sets---creating-session-scoped-named-sets"></a>Именованные наборы - Создание областью действия сеанса многомерных Выражений именованных наборов
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Для создания именованного набора, доступного в сеансе многомерных выражений, используется инструкция [CREATE SET](../../../mdx/mdx-data-definition-create-set.md). Именованный набор, созданный с помощью инструкции CREATE SET, удаляется только при закрытии сеанса многомерных выражений.  
  
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
 [Создание областью действия запроса именованных наборов & #40; Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
