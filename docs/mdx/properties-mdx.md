---
title: Свойства (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a9aa2ab3fbfdbe10246e0dcf8758cfcf7732375
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893675"
---
# <a name="properties-mdx"></a>Properties (многомерные выражения)


  Возвращает строку или строго типизированное значение, содержащее значение свойства элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Property_Name*  
 Допустимое строковое выражение, обозначающее имя свойства элемента.  
  
## <a name="remarks"></a>Примечания  
 Функция **Properties** возвращает значение указанного элемента для указанного свойства элемента. Свойством элемента может быть любое из внутренних свойств элемента, например **имя**, **идентификатор**, **ключ**или **заголовок**, либо может быть определяемым пользователем свойством элемента. Дополнительные сведения см. в разделе [внутренние свойства &#40;элементов&#41; многомерные](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties) выражения и [определяемые &#40;пользователем&#41;свойства элементов многомерные выражения](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties).  
  
 По умолчанию значение приводится к строке. Если указан параметр **Type** , возвращаемое значение является строго типизированным.  
  
-   Для свойства встроенного типа тип возвращаемого значения совпадает с типом свойства элемента.  
  
-   Если тип свойства определяется пользователем, тип возвращаемого значения совпадает с типом возвращаемого значения функции **MemberValue** .  
  
> [!NOTE]  
>  Функция Properties ('Key') возвращает тот же результат, что и Key0, за исключением составных ключей. Функция Properties ('Key') возвращает значение NULL для составных ключей. Используйте синтаксис ключа*x* для составных ключей, как показано в примере. Функции Properties ('Key0'), Properties ('Key1'), Properties ('Key2') и т. д. совместно формируют составной ключ.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются и внутренние, и пользовательские свойства элемента, аргумент TYPED используется, чтобы вернуть строго типизированное значение свойства элемента Day Name.  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT {Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере показано использование свойства*x* ключа.  
  
```  
WITH   
MEMBER Measures.MemberKey AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key')  
MEMBER Measures.MemberKey0 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key0')  
MEMBER Measures.MemberKey1 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key1')  
  
SELECT {Measures.MemberKey  
   , Measures.MemberKey0  
   , Measures.MemberKey1     
   }  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Использование свойств элементов (многомерные выражения)](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
