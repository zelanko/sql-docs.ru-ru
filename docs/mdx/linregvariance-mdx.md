---
title: "LinRegVariance (многомерные Выражения) | Документы Microsoft"
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
- LINREGVARIANCE
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegVariance function
ms.assetid: 09803510-2d71-401b-970e-bbdcac06558d
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 30ce6e0e7f43be71824734b7ab9790007a9f4763
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="linregvariance-mdx"></a>LinRegVariance (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вычисляет линейную регрессию набора и возвращает дисперсию, связанную с линией регрессии y = ax + b.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinRegVariance(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] ] )  
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
  
 **LinRegVariance** функция вычисляет указанный набор первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет указанный набор со вторым числовым выражением (если оно указано), чтобы получить значения для оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X. Аргумент для оси X часто опускается при работе с измерением времени.  
  
 Получив набор точек, **LinRegVariance** функция возвращает статистическую дисперсию, описывающую степень согласия линейного уравнения с точки.  
  
> [!NOTE]  
>  **LinRegVariance** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает статистическую дисперсию, описывающую степень согласия линейного уравнения с мерами розничных продаж по магазинам и общего объема продаж.  
  
```  
LinRegVariance(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

