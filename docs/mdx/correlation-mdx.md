---
title: Correlation (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e4b53ff01dc6cf0d62b334e95ac8a474f969f5f9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577456"
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
  
## <a name="remarks"></a>Примечания  
 **Корреляции** функция вычисляет коэффициент корреляции двух пар значений вычислением заданный набор относительно первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет заданный набор относительно второго числового выражения, если оно определено, для получения значений по оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячейки в заданном наборе в качестве значений по оси X.  
  
> [!NOTE]  
>  **Корреляции** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
