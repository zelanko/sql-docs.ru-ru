---
title: + (Добавить) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b13784b757241cc99ee58bec949348017b048e64
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576976"
---
# <a name="-add-mdx"></a>+ (сложение) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет арифметическое действие сложения двух чисел.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric_Expression + Numeric_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *Числовое выражение*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение с типом данных параметра, имеющего более высокий приоритет.  
  
## <a name="remarks"></a>Примечания  
 Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения. Если результатом вычисления одного выражения является значение NULL, оператор возвращает результат вычисления другого выражения.  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
