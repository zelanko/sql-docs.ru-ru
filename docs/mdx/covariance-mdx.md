---
title: "Covariance (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COVARIANCE
dev_langs: kbMDX
helpviewer_keywords: Covariance function
ms.assetid: 5faf6742-62db-4c5c-8797-096bf1cab273
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3fc176efc054f1adf5081dd84d349dfa136fd4b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="covariance-mdx"></a>Covariance (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает ковариацию совокупности значений пар X-Y, вычисленных из набора с помощью формулы смещенной совокупности (разделенную на количество пар X-Y).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Covariance(Set_Expression,Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression_y*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси Y.  
  
 *Numeric_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси X.  
  
## <a name="remarks"></a>Remarks  
 **Ковариация** функция вычисляет указанный набор с первым числовым выражением, чтобы получить значения для оси y. Затем функция вычисляет указанный набор со вторым числовым выражением (если оно указано), чтобы получить значения для оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X.  
  
 **Ковариация** функции используется формула смещенной совокупности. Это отличается от [CovarianceN](../mdx/covariancen-mdx.md) функции, использующей формулу несмещенной совокупности (делением на количество пар x-y, а затем вычитания 1).  
  
> [!NOTE]  
>  **Ковариация** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения учитываются. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование функции внутри функции Covariance:  
  
```  
WITH   
MEMBER [Measures].[CovarianceDemo] AS  
COVARIANCE([Date].[Date].[Date].Members, [Measures].[Internet Sales Amount], [Measures].[Internet Order Count])   
SELECT {[Measures].[CovarianceDemo]} ON 0   
FROM  
[Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
