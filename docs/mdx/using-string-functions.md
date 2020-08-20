---
description: Использование строковых функций
title: Использование строковых функций | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2160662a5e8fe9e89e133e053cca820fc60a66e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500487"
---
# <a name="using-string-functions"></a>Использование строковых функций


  Строковые функции работают практически с любыми объектами языка многомерных выражений. В хранимых процедурах строковые функции применяются в основном для преобразования объекта в строковое представление. Кроме того, строковые функции служат для вычисления строковых выражений над объектами, возвращающих значение.  
  
 Наиболее часто используемыми строковыми функциями являются **Name** и **UniqueName**. Они возвращают соответственно имя и уникальное имя объекта. В основном они используются при отладке вычислений, чтобы выяснить, какой элемент возвращает та или иная функция.  
  
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
  
 Функцию **Generate** можно использовать для выполнения строковой функции для каждого члена набора и объединения результатов. Это может быть полезно и при отладке вычислений, так как позволяет видеть содержимое набора. Следующий пример демонстрирует такое использование функции:  
  
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
  
 Другая группа широко используемых строковых функций — это функции, которые позволяют привести строковое значение, содержащее уникальное имя объекта или выражение, которое разрешается в объект, к самому объекту. В следующем примере запроса показано, как это делают функции **StrToMember** и **StrToSet** :  
  
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
>  Функции **StrToMember** и **StrToSet** следует использовать с осторожностью. Их использование в определениях вычислений может привести к снижению производительности запросов.  
  
## <a name="see-also"></a>См. также  
 [Создание &#40;многомерных выражений&#41;](../mdx/generate-mdx.md)   
 [Имя &#40;&#41;многомерных выражений ](../mdx/name-mdx.md)   
 [Уникальное &#40;&#41;многомерных выражений ](../mdx/uniquename-mdx.md)   
 [Функции &#40;синтаксиса многомерных выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Использование хранимых процедур &#40;&#41;многомерных выражений ](../mdx/using-stored-procedures-mdx.md)   
 [StrToMember &#40;&#41;многомерных выражений ](../mdx/strtomember-mdx.md)   
 [StrToSet &#40;&#41;многомерных выражений ](../mdx/strtoset-mdx.md)  
  
  
