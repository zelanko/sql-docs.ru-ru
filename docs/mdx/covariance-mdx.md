---
description: Covariance (многомерные выражения)
title: Ковариация (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 32471a48f0a669f7b72b5946f07403d6851dfb74
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500537"
---
# <a name="covariance-mdx"></a>Covariance (многомерные выражения)


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
 Функция **ковариации** вычисляет указанный набор для первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет указанный набор со вторым числовым выражением (если оно указано), чтобы получить значения для оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X.  
  
 Функция **ковариации** использует формулу смещенной совокупности. Это отличается от функции [CovarianceN](../mdx/covariancen-mdx.md) , которая использует формулу несмещенной совокупности (деление количества пар x-y, а затем вычитание 1).  
  
> [!NOTE]  
>  Функция **ковариации** игнорирует пустые ячейки или ячейки, содержащие текст или логические значения, не учитываются. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
