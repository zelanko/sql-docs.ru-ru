---
title: StrToValue (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cad8fec605a56a60cfcc7024739225e474fd42f8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036689"
---
# <a name="strtovalue-mdx"></a>StrToValue (многомерные выражения)


  Возвращает числовое значение, заданное в формате строки МНОГОМЕРных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *MDX_Expression*  
 Допустимое строковое выражение, разрешающееся (напрямую или косвенно) в одну ячейку.  
  
## <a name="remarks"></a>Remarks  
 Функция **StrToValue** возвращает числовое значение, ЗАданное многомерным выражением. Функция **StrToValue** обычно используется с определяемыми пользователем функциями для возвращения многомерного выражения из внешней функции обратно в ИНСТРУКЦИю многомерных выражений, которая может быть разрешена в одну ячейку.  
  
-   При использовании флага CONSTRAINED многомерное выражение должно содержать только скалярное значение. Флаг CONSTRAINED позволяет снизить вероятность атак через указанную строку. Если указано МНОГОМЕРное выражение, которое не разрешается напрямую в скалярное значение, появляется следующее сообщение об ошибке: "нарушены ограничения, установленные флагом CONSTRAINED в функции STRTOVALUE".  
  
-   Без флага CONSTRAINED можно использовать многомерные выражения любой сложности, если они разрешаются в допустимое многомерной выражение, возвращающее одну ячейку.  
  
> [!NOTE]  
>  Возвращение результата многомерного выражения в виде числового значения полезно использовать, если значение хранится в текстовом виде и требуется выполнить арифметические операции над возвращаемыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере функция **StrToValue** используется для возврата веса каждого велосипеда в качестве значения.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
