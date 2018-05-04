---
title: Операторы работы с наборами | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: 860a95d1e16a2404a13812ca77cf0c0a46ae7ead
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-operators"></a>Операторы наборов
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  В многомерных выражениях операторы наборов служат для выполнения операций над элементами и наборами, возвращающими набор. Операторы наборов часто используются в многомерных выражениях вместо нескольких функций наборов.  
  
 В многомерных выражениях поддерживаются операторы наборов, перечисленные в следующей таблице.  
  
|Оператор|Описание|  
|--------------|-----------------|  
|[- (исключение)](../mdx/except-mdx-operator.md)|Возвращает разность двух наборов, удаляя повторяющиеся элементы.<br /><br /> Этот оператор функционально эквивалентен [за исключением](../mdx/except-mdx-function.md) функции.|  
|[* (перекрестное соединение)](../mdx/crossjoin-mdx-operator-reference.md)|Возвращает перекрестное произведение двух наборов.<br /><br /> Этот оператор функционально эквивалентен [Crossjoin](../mdx/crossjoin-mdx.md) функции.|  
|[: (диапазон)](../mdx/range-mdx.md)|Возвращает естественно упорядоченный набор, ограниченный двумя указанными элементами. Набор содержит все элементы между ними и сами конечные элементы.|  
|[+ (объединение множеств)](../mdx/union-mdx-operator-reference.md)|Возвращает объединение двух наборов, исключая повторяющиеся элементы.<br /><br /> Этот оператор функционально эквивалентен [объединения &#40;многомерных Выражений&#41; ](../mdx/union-mdx.md) функции.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений & #40; Многомерные Выражения & #41;](../mdx/mdx-function-reference-mdx.md)   
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40;синтаксис многомерных Выражений&#41;](../mdx/operators-mdx-syntax.md)  
  
  
