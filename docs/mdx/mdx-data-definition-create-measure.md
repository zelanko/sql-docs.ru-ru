---
title: Инструкция CREATE MEASURE (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 37a8b8ef757184e7467c3551148c8c149bb45097
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144460"
---
# <a name="mdx-data-definition---create-measure"></a>Определение данных многомерных выражений — CREATE MEASURE


  Создает меру в табличной модели.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Имя_таблицы*  
 Допустимый строковый литерал, содержащий имя таблицы, в которой создается мера.  
  
 *Measure_Name*  
 Допустимый строковый литерал, содержащий имя меры.  
  
 *DAX_Expression*  
 Допустимое выражение DAX, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Примечания  
 *Measure_Name* должно быть заключено в квадратные скобки.  
  
 Инструкция CREATE MEASURE используется только внутри определения скрипта многомерных Выражений; см. в разделе [элемент MdxScript &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/mdxscript-element-assl).  
  
 Можно также определить вычисляемый элемент для использования только в одном запросе. Для определения вычисляемого элемента, ограниченного рамками одного запроса, используется предложение WITH в инструкции SELECT. Дополнительные сведения см. в разделе [построение мер в многомерных Выражениях](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
## <a name="see-also"></a>См. также  
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
