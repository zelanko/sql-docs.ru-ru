---
title: Если инструкция (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4975c455b942f053287b344a956a0083c8ca4e1a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187513"
---
# <a name="mdx-scripting---if"></a>Сценарии многомерных выражений — IF


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
 Используйте инструкцию IF для потока управления, которая отличается от [IIf &#40;многомерных Выражений&#41; ](../mdx/iif-mdx.md) функции и [оператор CASE &#40;многомерных Выражений&#41; ](../mdx/case-statement-mdx.md) , может использоваться только для возврата значений или объектов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере область ограничена уровнем «Страна» иерархии «География заказчика» в измерении «Заказчики». Если текущая мера — это «Сумма продаж через Интернет», то сумме продаж через Интернет присваивается значение 10.  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
