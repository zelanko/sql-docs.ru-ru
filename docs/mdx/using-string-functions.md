---
title: Использование строковых функций | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 74eec478baad335cb5be6a78ec1faea2d15030ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037992"
---
# <a name="using-string-functions"></a>Использование строковых функций


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
  
 **Формирования** функция может использоваться для выполнения строковой функции над каждым элементом набора и объединить результаты. Это может быть полезно и при отладке вычислений, так как позволяет видеть содержимое набора. Следующий пример демонстрирует такое использование функции:  
  
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
  
 Другая группа широко используемых строковых функций — это функции, которые позволяют привести строковое значение, содержащее уникальное имя объекта или выражение, которое разрешается в объект, к самому объекту. В следующем примере запроса показано, как **StrToMember** и **StrToSet** функции этого:  
  
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
  
## <a name="see-also"></a>См. также  
 [Создать &#40;многомерных Выражений&#41;](../mdx/generate-mdx.md)   
 [Имя &#40;многомерных Выражений&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;многомерных Выражений&#41;](../mdx/uniquename-mdx.md)   
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Использование хранимых процедур &#40;многомерных Выражений&#41;](../mdx/using-stored-procedures-mdx.md)   
 [StrToMember &#40;многомерных Выражений&#41;](../mdx/strtomember-mdx.md)   
 [StrToSet &#40;многомерных Выражений&#41;](../mdx/strtoset-mdx.md)  
  
  
