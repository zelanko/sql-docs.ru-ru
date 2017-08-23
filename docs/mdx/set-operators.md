---
title: "Операторы работы с наборами | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ed67b969d53eeb65009926cade623d2b87b9e175
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="set-operators"></a>Операторы наборов
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В многомерных выражениях операторы наборов служат для выполнения операций над элементами и наборами, возвращающими набор. Операторы наборов часто используются в многомерных выражениях вместо нескольких функций наборов.  
  
 В многомерных выражениях поддерживаются операторы наборов, перечисленные в следующей таблице.  
  
|Оператор|Description|  
|--------------|-----------------|  
|[-(За исключением)](../mdx/except-mdx-operator.md)|Возвращает разность двух наборов, удаляя повторяющиеся элементы.<br /><br /> Этот оператор функционально эквивалентен [за исключением](../mdx/except-mdx-function.md) функции.|  
|[* (Перекрестное соединение)](../mdx/crossjoin-mdx-operator-reference.md)|Возвращает перекрестное произведение двух наборов.<br /><br /> Этот оператор функционально эквивалентен [Crossjoin](../mdx/crossjoin-mdx.md) функции.|  
|[: (Диапазона)](../mdx/range-mdx.md)|Возвращает естественно упорядоченный набор, ограниченный двумя указанными элементами. Набор содержит все элементы между ними и сами конечные элементы.|  
|[+ (Объединение)](../mdx/union-mdx-operator-reference.md)|Возвращает объединение двух наборов, исключая повторяющиеся элементы.<br /><br /> Этот оператор функционально эквивалентен [Union &#40; Многомерные Выражения &#41; ](../mdx/union-mdx.md) функции.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40; Синтаксис многомерных Выражений &#41;](../mdx/operators-mdx-syntax.md)  
  
  

