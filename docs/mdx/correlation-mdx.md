---
title: "Correlation (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 00f2e3380c1706805e111edbc24423ae49e3ab97
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="correlation-mdx"></a>Correlation (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
 **Корреляции** функция вычисляет коэффициент корреляции двух пар значений вычислением заданный набор относительно первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет заданный набор относительно второго числового выражения, если оно определено, для получения значений по оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячейки в заданном наборе в качестве значений по оси X.  
  
> [!NOTE]  
>  **Корреляции** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

