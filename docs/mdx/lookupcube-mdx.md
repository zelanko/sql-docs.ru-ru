---
title: LookupCube (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: b21de8eae8df0d591ab99038065a24ed85453ed1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="lookupcube-mdx"></a>LookupCube (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
