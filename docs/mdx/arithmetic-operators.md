---
title: Арифметические операторы | Документы Microsoft
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
- arithmetic operators
ms.assetid: 1dff3e20-fe9d-4155-bf06-27d6458188e9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6e835905fb1d51d4918c3d382ad6268925d469e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="arithmetic-operators"></a>Арифметические операторы
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Арифметические операторы в многомерных выражениях можно использовать для любых арифметических вычислений, в том числе сложения, вычитания, умножения и деления.  
  
 Многомерные выражения поддерживают арифметические операции, перечисленные в следующей таблице.  
  
|Оператор|Description|  
|--------------|-----------------|  
|[+ (сложение)](../mdx/add-mdx.md)|складывает два числа.|  
|[/ (Деление)](../mdx/divide-mdx-operator-reference.md)|Делит одно число на другое.|  
|[* (умножение)](../mdx/multiply-mdx.md)|Перемножает два числа.|  
|[- (вычитание)](../mdx/subtract-mdx.md)|Выполняет вычитание двух чисел.|  
|^ (возведение в степень)|Возводит одно число в степень, указанную другим числом.|  
  
> [!NOTE]  
>  Многомерное выражение не включает функцию для получения квадратного корня из числа. Чтобы получить квадратный корень из числа, возведите число в степень 0,5 с помощью оператора ^.  
  
## <a name="order-of-precedence"></a>Очередность выполнения  
 Очередность выполнения арифметических операций в многомерном выражении определяется следующими правилами.  
  
-   Если в выражении содержится более одного арифметического оператора, многомерное выражение выполняет в первую очередь умножение и деление, а затем вычитание и сложение.  
  
-   Если все арифметические операторы в выражении имеют одинаковую очередность, то действия выполняются слева направо.  
  
-   Выражения внутри скобок выполняются прежде всех других операторов.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40; Синтаксис многомерных Выражений &#41;](../mdx/operators-mdx-syntax.md)  
  
  
