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
manager: kfile
ms.openlocfilehash: 3a0c11acadcbdcadfd9398baff09db9292c87eb2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248130"
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
  
  
