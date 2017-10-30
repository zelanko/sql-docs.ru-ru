---
title: "LinRegIntercept (многомерные Выражения) | Документы Microsoft"
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
- LINREGINTERCEPT
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegIntercept function
ms.assetid: 6ef2527d-e519-4b66-b67e-131c5831234e
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 59e23a316aa99612861a3181b1254b04c8a09014
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="linregintercept-mdx"></a>LinRegIntercept (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вычисляет линейную регрессию набора и возвращает значение отрезка, отсекаемого x в линии регрессии y = ax + b.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinRegIntercept(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
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
  
 **LinRegIntercept** функция вычисляет заданный набор относительно первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет указанный набор со вторым числовым выражением (если оно указано), чтобы получить значения для оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X. Аргумент для оси X часто опускается при работе с измерением времени.  
  
 Получив набор точек, **LinRegIntercept** возвращается длина отрезка, отсекаемого линией регрессии (b в предыдущем уравнении).  
  
> [!NOTE]  
>  **LinRegIntercept** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается длина отрезка, отсекаемого линией регрессии, для мер объема розничных продаж и общего объема продаж.  
  
```  
LinRegIntercept(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

