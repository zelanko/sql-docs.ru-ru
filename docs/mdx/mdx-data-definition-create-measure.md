---
title: Инструкция CREATE MEASURE (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98ca479c266d9e8c25b2e75d8b15da1cd76a46aa
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579356"
---
# <a name="mdx-data-definition---create-measure"></a>Определения данных многомерных Выражений — создать МЕРУ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 Инструкция CREATE MEASURE может использоваться только внутри определения скрипта MDX; в разделе [элемент MdxScript &#40;ASSL&#41;](../analysis-services/scripting/objects/mdxscript-element-assl.md).  
  
 Можно также определить вычисляемый элемент для использования только в одном запросе. Для определения вычисляемого элемента, ограниченного рамками одного запроса, используется предложение WITH в инструкции SELECT. Дополнительные сведения см. в разделе [построение мер в многомерных Выражениях](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
## <a name="see-also"></a>См. также  
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
