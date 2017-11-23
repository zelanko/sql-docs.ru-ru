---
title: "Использование строковых функций | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: string functions
ms.assetid: 962e820a-a1f9-49b5-90f0-a05261e6682b
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5838cb18091adab8ee4e8b2c0a43042001c530dc
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="using-string-functions"></a>Использование строковых функций
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Строковые функции работают практически с любыми объектами языка многомерных выражений. В хранимых процедурах строковые функции применяются в основном для преобразования объекта в строковое представление. Кроме того, строковые функции служат для вычисления строковых выражений над объектами, возвращающих значение.  
  
 Самые распространенные строковые функции являются **имя** и **Uniquename**. Они возвращают соответственно имя и уникальное имя объекта. В основном они используются при отладке вычислений, чтобы выяснить, какой элемент возвращает та или иная функция.  
  
## <a name="examples"></a>Примеры  
 Запросы в следующем примере демонстрируют использование этих функций:  
  
 `WITH`  
  
 `//Returns the name of the current Product on rows`  
  
 `MEMBER [Measures].[ProductName] AS [Product].[Product].CurrentMember.Name`  
  
 `//Returns the uniquename of the current Product on rows`  
  
 `MEMBER [Measures].[ProductUniqueName] AS [Product].[Product].CurrentMember.Uniquename`  
  
 `//Returns the name of the Product dimension`  
  
 `MEMBER [Measures].[ProductDimensionName] AS [Product].Name`  
  
 `SELECT  {[Measures].[ProductName],[Measures].[ProductUniqueName],[Measures].[ProductDimensionName]}`  
  
 `ON COLUMNS,`  
  
 `[Product].[Product].MEMBERS  ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 **Формирования** функцию можно использовать для выполнения строковой функции над каждым элементом набора и объединить результаты. Это может быть полезно и при отладке вычислений, так как позволяет видеть содержимое набора. Следующий пример демонстрирует такое использование функции:  
  
 `WITH`  
  
 `//Returns the names of the current Product and its ancestors up to the All Member`  
  
 `MEMBER [Measures].[AncestorNames] AS`  
  
 `GENERATE(`  
  
 `ASCENDANTS([Product].[Product Categories].CurrentMember)`  
  
 `, [Product].[Product Categories].CurrentMember.Name, ", ")`  
  
 `SELECT`  
  
 `{[Measures].[AncestorNames]}`  
  
 `ON COLUMNS,`  
  
 `[Product].[Product Categories].MEMBERS  ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Другая группа широко используемых строковых функций — это функции, которые позволяют привести строковое значение, содержащее уникальное имя объекта или выражение, которое разрешается в объект, к самому объекту. В следующем примере запроса показано, как **StrToMember** и **StrToSet** это делается с помощью функций:  
  
 `SELECT`  
  
 `{StrToMember("[Measures].[Inter" + "net Sales Amount]")}`  
  
 `ON COLUMNS,`  
  
 `StrToSet("{`  
  
 `[Product].[Product Categories].[Category].&[3],`  
  
 `[Product].[Product Categories].[Product].&[477],`  
  
 `[Product].[Product Categories].[Product].&[788],`  
  
 `[Product].[Product Categories].[Product].&[708],`  
  
 `[Product].[Product Categories].[Product].&[711]`  
  
 `}")`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
> [!NOTE]  
>  **StrToMember** и **StrToSet** функции следует использовать с осторожностью. Их использование в определениях вычислений может привести к снижению производительности запросов.  
  
## <a name="see-also"></a>См. также:  
 [Создать &#40; Многомерные Выражения &#41;](../mdx/generate-mdx.md)   
 [Имя &#40; Многомерные Выражения &#41;](../mdx/name-mdx.md)   
 [UniqueName &#40; Многомерные Выражения &#41;](../mdx/uniquename-mdx.md)   
 [Функции &#40; Синтаксис многомерных Выражений &#41;](../mdx/functions-mdx-syntax.md)   
 [С помощью хранимых процедур &#40; Многомерные Выражения &#41;](../mdx/using-stored-procedures-mdx.md)   
 [StrToMember &#40; Многомерные Выражения &#41;](../mdx/strtomember-mdx.md)   
 [StrToSet &#40; Многомерные Выражения &#41;](../mdx/strtoset-mdx.md)  
  
  
