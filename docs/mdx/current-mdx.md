---
title: Current (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e30e2a7940223c7872151d96f05ff79ca919decf
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577696"
---
# <a name="current-mdx"></a>Current (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает текущий кортеж из набора во время выполнения цикла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 На каждом шаге выполнения цикла текущим является тот кортеж, над которым производятся действия на этом шаге. **Текущей** функция возвращает этот кортеж. Функция допустима только во время итерации по набору.  
  
 Включить функции многомерных Выражений, которые проходят через набор [формирования](../mdx/generate-mdx.md) функции.  
  
> [!NOTE]  
>  Функция работает только с имеющими имя наборами — используя псевдоним набора или определяя именованный набор.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать **текущей** функции внутри **формирования**:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of all Calendar Years crossjoined with`  
  
 `//all Product Categories`  
  
 `SET MyTuples AS CROSSJOIN(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `//Iterates through each tuple in the set and returns the name of the Calendar`  
  
 `//Year in each tuple`  
  
 `MEMBER MEASURES.CURRENTDEMO AS`  
  
 `GENERATE(MyTuples, MyTuples.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
