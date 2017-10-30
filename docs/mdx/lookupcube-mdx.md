---
title: "LookupCube (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOOKUPCUBE
dev_langs:
- kbMDX
helpviewer_keywords:
- LookupCube function
ms.assetid: 243fa101-328a-4016-86e0-d8b5977e15a9
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41aed2def9e470d39f006b314f51dbb61bf63b47
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="lookupcube-mdx"></a>LookupCube (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, **LookupCube** функция вычисляет указанное числовое выражение в заданном кубе и возвращает числовое значение.  
  
 Если строковое выражение указано, **LookupCube** функция вычисляет указанного строкового выражения в заданном кубе и возвращает строковое значение.  
  
 **LookupCube** функция применяется к кубам внутри той же базе данных как исходного куба, на котором запрос многомерных Выражений, который содержит **LookupCube** функция выполняется.  
  
> [!IMPORTANT]  
>  В числовом или строковом выражении необходимо указывать все необходимые текущие элементы, поскольку контекст текущего запроса не переносятся в запрашиваемый куб.  
  
 Вычисления с помощью **LookupCube** функция большой вероятностью может страдать от низкой производительности. Вместо того чтобы использовать эту функцию, попробуйте переделать это решение таким образом, чтобы все необходимые данные находились в одном кубе.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано использование функции LookupCube:  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

