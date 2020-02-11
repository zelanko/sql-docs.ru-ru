---
title: DefaultMember (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0b5039ae62eac25d698442d4aeb92ad3c4ebc3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892902"
---
# <a name="defaultmember-mdx"></a>DefaultMember (многомерные выражения)


  Возвращает элемент иерархии по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Remarks  
 Элемент по умолчанию атрибута используется для оценки выражений, когда атрибут не включен в запрос.  
  
## <a name="example"></a>Пример  
 В следующем примере функция **DefaultMember** используется вместе с функцией **Name** для возврата элемента по умолчанию для измерения целевой валюты в кубе Adventure Works. Пример возвращает **доллар США**. Функция **Name** используется для возвращения имени меры, а не свойства по умолчанию меры, которое является **значением**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)   
 [Определение элемента по умолчанию](https://docs.microsoft.com/analysis-services/multidimensional-models/attribute-properties-define-a-default-member)  
  
  
