---
title: AddCalculatedMembers (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5a9c154588c359c942e6d64a0afdadff981e1bf5
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576936"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор, созданный путем добавления вычисляемых элементов в указанный набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию в языке многомерных выражений вычисляемые элементы исключаются при вычислении функций набора. **AddCalculatedMembers** функция просматривает выражение набора, указанного в *Set_Expression,* и включает вычисляемые одноуровневые элементы, содержащиеся в области данного выражения набора.  
  
> [!NOTE]  
>  Эту функцию можно использовать только для одномерных выражений наборов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование этой функции.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 В следующем примере возвращается `Measures.[Unit Price]` вместе со всеми вычисляемыми элементами в **меры** измерения, от **Adventure Works** куба.  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
