---
title: LinkMember (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8a00388e067878d9c2165cbae6844f8020b7c63e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905605"
---
# <a name="linkmember-mdx"></a>LinkMember (многомерные выражения)


  Возвращает элемент, эквивалентный заданному элементу в указанной иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Remarks  
 Функция **LinkMember** Возвращает элемент из указанной иерархии, который соответствует ключевым значениям на каждом уровне указанного элемента в связанной иерархии. Атрибуты каждого уровня должны иметь одинаковое количество элементов ключа и тип данных. В искусственных иерархиях, если имеется более чем одно совпадение значения ключа атрибута, будет возвращена ошибка или неопределенный результат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция **LinkMember** используется для возврата меры по умолчанию в кубе Adventure Works для предков из 1 июля 2002 элемента иерархии атрибута Date. Date в иерархии Calendar.  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Hierarchize &#40;&#41;многомерных выражений](../mdx/hierarchize-mdx.md)   
 [Предков &#40;&#41;многомерных выражений](../mdx/ascendants-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
