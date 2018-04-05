---
title: Correlation (многомерные Выражения) | Документы Microsoft
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
f1_keywords:
- CORRELATION
dev_langs:
- kbMDX
helpviewer_keywords:
- Correlation function
ms.assetid: 9b3662c9-95a1-4644-b952-9460fe0cf160
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 349bc24c61d538fcb5b6c4a14b6bd02f52510184
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="correlation-mdx"></a>Correlation (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает коэффициент корреляции пар значений x-y, рассчитанных по набору.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Correlation( Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression_y*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси Y.  
  
 *Numeric_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси X.  
  
## <a name="remarks"></a>Remarks  
 **Корреляции** функция вычисляет коэффициент корреляции двух пар значений вычислением заданный набор относительно первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет заданный набор относительно второго числового выражения, если оно определено, для получения значений по оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячейки в заданном наборе в качестве значений по оси X.  
  
> [!NOTE]  
>  **Корреляции** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
