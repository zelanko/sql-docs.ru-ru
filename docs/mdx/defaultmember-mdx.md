---
title: DefaultMember (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c5843ec42cf4ba712a2e55c9cc96dd6f482c0760
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047091"
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
  
## <a name="remarks"></a>Примечания  
 Элемент по умолчанию атрибута используется для оценки выражений, когда атрибут не включен в запрос.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **DefaultMember** функция в сочетании с **имя** для возвращения элемента по умолчанию для измерения Destination Currency в кубе Adventure Works. В примере возвращается **доллар США**. **Имя** функция используется для возвращения имени меры, а не свойство по умолчанию измерения, который является **значение**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [Определение элемента по умолчанию](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
