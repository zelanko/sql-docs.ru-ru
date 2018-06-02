---
title: CoalesceEmpty (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cbd5928e859436b90b986e9e0ea0d09e91ccd664
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577316"
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Преобразовывает значения пустых ячеек в заданные непустые значения, которые могут быть числами или строками.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric syntax  
CoalesceEmpty( Numeric_Expression1 [ ,Numeric_Expression2,...n] )  
  
String syntax  
CoalesceEmpty(String_Expression1 [ ,String_Expression2,...n] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Numeric_Expression1*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *Numeric_Expression2*  
 Допустимое числовое выражение, обычно являющееся заданной числовой величиной.  
  
 *Выражение String_Expression1*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *Выражение String_Expression2*  
 Допустимая строка выражения, обычно являющаяся указанным строковым значением, заменяющим значение NULL, возвращаемое первым строковым выражением.  
  
## <a name="remarks"></a>Примечания  
 Если один или несколько числовых выражений указаны, **CoalesceEmpty** функция возвращает числовое значение первого (слева направо) числового выражения, которое разрешается к непустому значению. Если ни одно из указанных числовых выражений не разрешается к непустому значению, функция возвращает пустое значение ячейки. Обычно значение второго численного выражения имеет численное значение, заменяющее значение NULL, возвращенное первым численным выражением.  
  
 Если одно или несколько строковых выражений определены, функция возвращает значение первого (слева направо) строкового выражения, которое разрешается к непустому значению. Если ни одно из заданных строковых выражений не разрешается к непустому значению, функция возвращает пустое значение ячейки. Обычно значение второго строкового выражения имеет значение, заменяющее значение NULL, возвращенное первым строковым выражением.  
  
 **CoalesceEmpty** функция может принимать только значения того же типа. Иными словами, все заданные выражения должны принимать значения либо только числовых типов данных и пустых значений ячеек, либо только строковых типов данных и пустых значений ячеек. В одном вызове этой функции нельзя смешивать числовые и строковые выражения.  
  
 Дополнительные сведения о пустых ячейках см. в документации по OLE DB.  
  
## <a name="example"></a>Пример  
 В следующем примере запрос **Adventure Works** куба. Запрос возвращает количество заказов каждого продукта и процентную долю каждого заказа по категориям. **CoalesceEmpty** функция обеспечивает представление значения null как нуль (0) при форматировании вычисляемых элементов.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
