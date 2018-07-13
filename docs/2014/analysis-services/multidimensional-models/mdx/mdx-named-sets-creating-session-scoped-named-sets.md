---
title: Создание с областью действия сеанса с именем наборами (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5a3d6a1fd35c91733b32ecc3244f0fd3bafe6a07
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167695"
---
# <a name="creating-session-scoped-named-sets-mdx"></a>Создание именованных наборов с областью действия сеанса (многомерные выражения)
  Для создания именованного набора, доступного в сеансе многомерных выражений, используется инструкция [CREATE SET](/sql/mdx/mdx-data-definition-create-set). Именованный набор, созданный с помощью инструкции CREATE SET, удаляется только при закрытии сеанса многомерных выражений.  
  
 Синтаксис ключевого слова WITH достаточно прост.  
  
> [!NOTE]  
>  Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](mdx-named-sets-building-named-sets.md).  
  
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
 [Создание, областью действия запроса именованных наборов с &#40;многомерных Выражений&#41;](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
