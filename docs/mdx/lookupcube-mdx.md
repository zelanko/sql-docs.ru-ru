---
title: LookupCube (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ec18b600c369de872df5f6eadf06ef6c30c88efa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68098515"
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
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, функция **LookupCube** вычисляет указанное числовое выражение в указанном кубе и возвращает полученное числовое значение.  
  
 Если строковое выражение указано, функция **LookupCube** вычисляет указанное строковое выражение в указанном кубе и возвращает результирующее строковое значение.  
  
 Функция **LookupCube** работает с кубами в той же базе данных, что и исходный куб, в котором выполняется запрос многомерных выражений, содержащий функцию **LookupCube** .  
  
> [!IMPORTANT]  
>  В числовом или строковом выражении необходимо указывать все необходимые текущие элементы, поскольку контекст текущего запроса не переносятся в запрашиваемый куб.  
  
 Любые вычисления, использующие функцию **LookupCube** , скорее всего, пострадает от низкой производительности. Вместо того чтобы использовать эту функцию, попробуйте переделать это решение таким образом, чтобы все необходимые данные находились в одном кубе.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано использование функции LookupCube:  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
