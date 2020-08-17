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
ms.openlocfilehash: cdbee6f6ede5e46926f1a8189792d86cf9e99f5b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387270"
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
  
 Инструкцию CREATE MEASURE можно использовать только в определении скрипта многомерных выражений. см. [элемент MdxScript &#40;&#41;ASSL ](https://docs.microsoft.com/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions).  
  
 Можно также определить вычисляемый элемент для использования только в одном запросе. Для определения вычисляемого элемента, ограниченного рамками одного запроса, используется предложение WITH в инструкции SELECT. Дополнительные сведения см. [в разделе Создание мер в многомерных выражениях](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
