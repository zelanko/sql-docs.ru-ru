---
title: CoalesceEmpty (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f760220b02396591e684a83305111e487908d19b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
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
  
 *String_Expression1*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *String_Expression2*  
 Допустимая строка выражения, обычно являющаяся указанным строковым значением, заменяющим значение NULL, возвращаемое первым строковым выражением.  
  
## <a name="remarks"></a>Remarks  
 Если указано одно или несколько числовых выражений, функция **CoalesceEmpty** возвращает числовое значение первого числового выражения (слева направо), которое может быть разрешено в непустое значение. Если ни одно из указанных числовых выражений не разрешается к непустому значению, функция возвращает пустое значение ячейки. Обычно значение второго численного выражения имеет численное значение, заменяющее значение NULL, возвращенное первым численным выражением.  
  
 Если одно или несколько строковых выражений определены, функция возвращает значение первого (слева направо) строкового выражения, которое разрешается к непустому значению. Если ни одно из заданных строковых выражений не разрешается к непустому значению, функция возвращает пустое значение ячейки. Обычно значение второго строкового выражения имеет значение, заменяющее значение NULL, возвращенное первым строковым выражением.  
  
 Функция **CoalesceEmpty** может принимать только значения одного типа. Иными словами, все заданные выражения должны принимать значения либо только числовых типов данных и пустых значений ячеек, либо только строковых типов данных и пустых значений ячеек. В одном вызове этой функции нельзя смешивать числовые и строковые выражения.  
  
 Дополнительные сведения о пустых ячейках см. в документации по OLE DB.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется запрос к кубу **Adventure Works** . Запрос возвращает количество заказов каждого продукта и процентную долю каждого заказа по категориям. Функция **CoalesceEmpty** гарантирует, что значения null будут представлены как нули (0) при форматировании вычисляемых элементов.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
