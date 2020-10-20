---
description: Определение данных многомерных выражений — CREATE MEASURE
title: Инструкция CREATE MEASURE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d352a12a4567fc88d2d037862c4cab2f1cd20fe0
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193966"
---
# <a name="mdx-data-definition---create-measure"></a>Определение данных многомерных выражений — CREATE MEASURE


  Создает меру в табличной модели.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Table_Name*  
 Допустимый строковый литерал, содержащий имя таблицы, в которой создается мера.  
  
 *Measure_Name*  
 Допустимый строковый литерал, содержащий имя меры.  
  
 *DAX_Expression*  
 Допустимое выражение DAX, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Remarks  
 *Measure_Name* должны быть заключены в квадратные скобки.  
  
 Инструкцию CREATE MEASURE можно использовать только в определении скрипта многомерных выражений. см. [элемент MdxScript &#40;&#41;ASSL ](/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions).  
  
 Можно также определить вычисляемый элемент для использования только в одном запросе. Для определения вычисляемого элемента, ограниченного рамками одного запроса, используется предложение WITH в инструкции SELECT. Дополнительные сведения см. [в разделе Создание мер в многомерных выражениях](/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
