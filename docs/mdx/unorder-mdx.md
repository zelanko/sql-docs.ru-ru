---
title: Unorder (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b5e360c8f15eafba2b4565ca41a557c9e1ceda9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743453"
---
# <a name="unorder-mdx"></a>Unorder (многомерные выражения)


  Удаляет принудительное упорядочивание заданного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 **Unorder** функция удаляет упорядочение кортежей в наборе с любой другой функцией или инструкцией, такой как [порядок](../mdx/order-mdx.md) функции. Порядок кортежей в наборе, возвращаемом **Unorder** функции не определено.  
  
 **Unorder** функция используется в качестве подсказки для оптимизации запросов для обработки набора. Если порядок кортежей в наборе не важен для вычислений запроса, с помощью **Unorder** функции может улучшить производительность в таких случаях. Например [NonEmpty (многомерные Выражения)](../mdx/nonempty-mdx.md) может выполняться лучше, если предоставленный набор для этой функции неупорядочен, чем если [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] требуется сохранять порядок, хотя с [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], обработчик запросов пытается выполнить эту функцию автоматически для многих функций, таких как **сумма** и **статистические**. Увеличение производительности с помощью **Unorder** , вероятнее всего только заметно с очень большими наборами, состоящими из миллионов кортежей.  
  
## <a name="example"></a>Пример  
 Следующий псевдокод иллюстрирует синтаксис для этой функции.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
