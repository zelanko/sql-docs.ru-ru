---
title: Инструкция CREATE MEASURE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 02c6d29bbebcc794e72f4ca960e3d9259de7205b
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892144"
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
  
## <a name="remarks"></a>Примечания  
 *Measure_Name* должен быть заключен в квадратные скобки.  
  
 Инструкцию CREATE MEASURE можно использовать только в определении скрипта многомерных выражений. см. [элемент &#40;MdxScript&#41;ASSL](https://docs.microsoft.com/bi-reference/assl/objects/mdxscript-element-assl).  
  
 Можно также определить вычисляемый элемент для использования только в одном запросе. Для определения вычисляемого элемента, ограниченного рамками одного запроса, используется предложение WITH в инструкции SELECT. Дополнительные сведения см. [в разделе Создание мер в многомерных выражениях](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>См. также  
 [Многомерные выражения инструкций &#40;определения данных многомерных выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
