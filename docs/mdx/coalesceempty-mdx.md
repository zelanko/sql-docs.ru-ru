---
title: CoalesceEmpty (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f760220b02396591e684a83305111e487908d19b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006304"
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty (многомерные выражения)


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
  
 **CoalesceEmpty** функция может принимать значения только одного типа. Иными словами, все заданные выражения должны принимать значения либо только числовых типов данных и пустых значений ячеек, либо только строковых типов данных и пустых значений ячеек. В одном вызове этой функции нельзя смешивать числовые и строковые выражения.  
  
 Дополнительные сведения о пустых ячейках см. в документации по OLE DB.  
  
## <a name="example"></a>Пример  
 В следующем примере запрос **Adventure Works** куба. Запрос возвращает количество заказов каждого продукта и процентную долю каждого заказа по категориям. **CoalesceEmpty** функция гарантирует, что значения null отображаются в виде нуля (0) при форматировании вычисляемых элементов.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
