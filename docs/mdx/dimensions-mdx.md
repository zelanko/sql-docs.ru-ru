---
title: Измерения (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84d5ab0caa22c6f35f3e7b790dbfb3348df8ceb1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67999964"
---
# <a name="dimensions-mdx"></a>Dimensions (многомерные выражения)


  Возвращает иерархию, указанную числовым или строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Number*  
 Допустимое числовое выражение, указывающее номер иерархии.  
  
 *Hierarchy_Name*  
 Допустимое строковое выражение, указывающее имя иерархии.  
  
## <a name="remarks"></a>Remarks  
 Если указан номер иерархии, функция **dimensions** возвращает иерархию, в которой Отсчитываемая от нуля позицией в Кубе задано значение иерархии.  
  
 Если указано имя иерархии, функция **dimensions** возвращает указанную иерархию. Как правило, эта строковая версия функции **dimensions** используется с определяемыми пользователем функциями.  
  
> [!NOTE]  
>  Измерение **Measures** всегда представлено `Dimensions(0)`.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах используется функция **dimensions** для возврата имени, количества уровней и числа элементов указанной иерархии с использованием как числового выражения, так и строкового выражения.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
