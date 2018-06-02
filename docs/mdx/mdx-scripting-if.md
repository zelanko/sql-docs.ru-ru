---
title: Если инструкция (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e7426c609de80ab249cd71e4364979ff07165598
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579866"
---
# <a name="mdx-scripting---if"></a>Скрипты многомерных Выражений: Если
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет инструкцию, если условие истинно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Многомерное выражение, принимающее логическое значение TRUE или FALSE.  
  
 *Назначение*  
 Многомерное выражение, присваивающее значение вложенному кубу или вычисляемому свойству.  
  
## <a name="remarks"></a>Примечания  
 Используйте инструкцию IF для потока управления, который в отличие от [IIf &#40;многомерных Выражений&#41; ](../mdx/iif-mdx.md) функции и [инструкции CASE &#40;многомерных Выражений&#41; ](../mdx/case-statement-mdx.md) , может использоваться только для возвращения значений или объектов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере область ограничена уровнем «Страна» иерархии «География заказчика» в измерении «Заказчики». Если текущая мера — это «Сумма продаж через Интернет», то сумме продаж через Интернет присваивается значение 10.  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
