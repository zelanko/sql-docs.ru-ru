---
title: Свойства (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b564d11696999ec2dbd778d15a3e881cab415259
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581136"
---
# <a name="properties-mdx"></a>Properties (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает строку или строго типизированное значение, содержащее значение свойства элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Property_name*  
 Допустимое строковое выражение, обозначающее имя свойства элемента.  
  
## <a name="remarks"></a>Примечания  
 **Свойства** функция возвращает значение указанного элемента для указанного свойства элемента. Свойство элемента может быть любой внутренние свойства элементов, таких как **имя**, **идентификатор**, **ключ**, или **заголовок**, или он может быть свойством определяемого пользователем элемента. Дополнительные сведения см. в разделе [внутренние свойства элементов &#40;многомерных Выражений&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) и [определяемые пользователем свойства элементов &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
 По умолчанию значение приводится к строке. Если **ТИПИЗИРОВАННОГО** указан, возвращаемое значение является типобезопасным.  
  
-   Для свойства встроенного типа тип возвращаемого значения совпадает с типом свойства элемента.  
  
-   Если тип свойства является определяемой пользователем, тип возвращаемого значения совпадает тип возвращаемого значения **MemberValue** функции.  
  
> [!NOTE]  
>  Функция Properties ('Key') возвращает тот же результат, что и Key0, за исключением составных ключей. Функция Properties ('Key') возвращает значение NULL для составных ключей. С помощью клавиши*x* синтаксис для составных ключей, как это показано в примере. Функции Properties ('Key0'), Properties ('Key1'), Properties ('Key2') и т. д. совместно формируют составной ключ.  
  
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
  
 В следующем примере показано использование свойства KEY*x* свойство.  
  
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
 [Использование свойств элементов &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
