---
title: Оператор IF (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 41bd34fbd3d296f4aa38877e6d26e25eba9ae726
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138694"
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
  
 *сваивать*  
 Многомерное выражение, присваивающее значение вложенному кубу или вычисляемому свойству.  
  
## <a name="remarks"></a>Remarks  
 Используйте оператор IF для потока управления, который отличается от функции [IIf &#40;многомерных выражений&#41;](../mdx/iif-mdx.md) и [оператора CASE &#40;MDX&#41;](../mdx/case-statement-mdx.md) , который может использоваться только для возвращения значений или объектов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере область ограничена уровнем «Страна» иерархии «География заказчика» в измерении «Заказчики». Если текущая мера — это «Сумма продаж через Интернет», то сумме продаж через Интернет присваивается значение 10.  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
