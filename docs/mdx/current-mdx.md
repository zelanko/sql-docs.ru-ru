---
title: Current (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 821d517419b90df44b7943a1e0edde12ef667b6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68047121"
---
# <a name="current-mdx"></a>Current (многомерные выражения)


  Возвращает текущий кортеж из набора во время выполнения цикла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 На каждом шаге выполнения цикла текущим является тот кортеж, над которым производятся действия на этом шаге. **Текущая** функция возвращает этот кортеж. Функция допустима только во время итерации по набору.  
  
 Функции многомерных выражений, перебираемые по набору, включают функцию [Generate](../mdx/generate-mdx.md) .  
  
> [!NOTE]  
>  Функция работает только с имеющими имя наборами — используя псевдоним набора или определяя именованный набор.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать **текущую** функцию внутри функции **Generate**:  
  
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
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
