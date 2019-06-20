---
title: LookupCube (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8f8338a542bf9e15816205930704c45a536a5629
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208517"
---
# <a name="lookupcube-mdx"></a>LookupCube (многомерные выражения)


  Возвращает значение многомерных выражений, вычисленное для другого указанного куба в той же базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric expression syntax  
LookupCube(Cube_Name, Numeric_Expression )  
  
String expression syntax  
LookupCube(Cube_Name, String_Expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, обозначающее имя куба.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *String_Expression*  
 Допустимое строковое выражение (обычно многомерное выражение над координатами ячейки), возвращающее строку.  
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, **LookupCube** функция вычисляет указанное числовое выражение в заданном кубе и возвращает числовое значение.  
  
 Если строковое выражение указано, **LookupCube** функция вычисляет указанного строкового выражения в заданном кубе и возвращает строковое значение.  
  
 **LookupCube** функция применяется к кубам внутри той же базе данных, как исходного куба, на котором запрос многомерных Выражений, который содержит **LookupCube** функция выполняется.  
  
> [!IMPORTANT]  
>  В числовом или строковом выражении необходимо указывать все необходимые текущие элементы, поскольку контекст текущего запроса не переносятся в запрашиваемый куб.  
  
 Вычисления с помощью **LookupCube** функция большой вероятностью может страдать от низкой производительности. Вместо того чтобы использовать эту функцию, попробуйте переделать это решение таким образом, чтобы все необходимые данные находились в одном кубе.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано использование функции LookupCube:  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
