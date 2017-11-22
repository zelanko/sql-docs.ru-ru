---
title: "LinRegPoint (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: LINREGPOINT
dev_langs: kbMDX
helpviewer_keywords: LinRegPoint function
ms.assetid: 28298d7c-2b8a-4423-ae52-9c2d6f0f0064
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d16da44758873659145058f9e5dab30fae8ff05c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="linregpoint-mdx"></a>LinRegPoint (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вычисляет линейную регрессию множества и возвращает значение *y-intercept* в линии регрессии y = ax + b для некоторого значения x.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Slice_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение над координатами ячейки), возвращающее число, которое представляет значения для оси среза.  
  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression_y*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси Y.  
  
 *Numeric_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси X.  
  
## <a name="remarks"></a>Замечания  
 Линейная регрессия, которая использует метод наименьших квадратов, вычисляет уравнение линии регрессии (то есть наиболее подходящую линию для последовательности точек). Линия регрессии имеет следующее уравнение, где — это наклон, а b-отсекаемый отрезок:  
  
 y = ax+b  
  
 **LinRegPoint** функция вычисляет заданный набор относительно второго численного выражения, чтобы получить значения для оси y. Затем функция вычисляет третье числовое выражение (если оно указано) над заданным набором, чтобы получить значения для оси X. Если третье числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X. Аргумент для оси X часто опускается при работе с измерением времени.  
  
 После вычисления линии линейной регрессии значение уравнения подставляется в первое числовое выражение и возвращается результат.  
  
> [!NOTE]  
>  **LinRegPoint** функция пропускает пустые ячейки и ячейки, содержащие текст. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается прогнозируемое значение показателя Unit Sales за последние 10 периодов на основе статистической связи показателей Unit Sales и Store Sales.  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
