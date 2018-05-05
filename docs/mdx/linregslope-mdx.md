---
title: LinRegSlope (многомерные Выражения) | Документы Microsoft
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
- LINREGSLOPE
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegSlope function
ms.assetid: dc61f941-b25d-4eef-9b25-75e03a1dd6de
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: e29d3cccd8a40499f0dc82debdfb5dda7a2ebd47
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="linregslope-mdx"></a>LinRegSlope (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Вычисляет линейную регрессию набора и возвращает значение наклона линии регрессии y = ax + b.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinRegSlope(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression_y*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси Y.  
  
 *Numeric_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси X.  
  
## <a name="remarks"></a>Замечания  
 Линейная регрессия, которая использует метод наименьших квадратов, вычисляет уравнение линии регрессии (то есть наиболее подходящую линию для последовательности точек). Линия регрессии имеет следующее уравнение, где — это наклон, а b-отсекаемый отрезок:  
  
 y = ax+b  
  
 **LinRegSlope** функция вычисляет заданный набор относительно первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет заданный набор относительно второго численного выражения, если оно определено, для получения значений для оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячейки в заданном наборе в качестве значений по оси X. Аргумент для оси X часто опускается при работе с измерением времени.  
  
 Получив набор точек, **LinRegSlope** функция возвращает угол наклона линии регрессии (в предыдущем уравнении).  
  
> [!NOTE]  
>  **LinRegSlope** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается наклон линии регрессии для мер розничных и оптовых продаж.  
  
```  
LinRegSlope(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
