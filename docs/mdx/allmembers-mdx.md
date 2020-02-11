---
title: AllMembers (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 770d66941af9b42be3c7b26f7e04a60d2a95cac2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017148"
---
# <a name="allmembers-mdx"></a>AllMembers (многомерные выражения)


  Вычисляет выражение иерархии или уровня и возвращает набор, содержащий все элементы заданной иерархии или уровня, включая все вычисляемые элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Remarks  
 Функция **AllMembers** возвращает набор, содержащий все элементы, включая вычисляемые элементы в указанной иерархии или уровне. Функция **AllMembers** возвращает вычисляемые элементы, даже если указанная иерархия или уровень не содержит видимых элементов.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения в этом случае разрешается в единственную видимую иерархию. Например, многомерное выражение `Measures.AllMembers` является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
> [!NOTE]  
>  Функция **AllMembers** семантически похожа на функцию [AddCalculatedMembers (многомерные выражения)](../mdx/addcalculatedmembers-mdx.md) .  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все элементы в иерархии атрибутов`Date].[Calendar Year]` [на оси столбцов, включая вычисляемые элементы, а также набор всех дочерних элементов иерархии `[Product].[Model Name]` атрибута на оси строк из куба **Adventure Works** .  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 В следующем примере возвращаются все элементы в измерении **Measures** на оси столбцов, включая все Вычисляемые элементы, а также набор всех дочерних элементов иерархии `[Product].[Model Name]` атрибута на оси строк из куба **Adventure Works** .  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [AddCalculatedMembers &#40;&#41;многомерных выражений](../mdx/addcalculatedmembers-mdx.md)   
 [Дочерние &#40;&#41;многомерных выражений](../mdx/children-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
