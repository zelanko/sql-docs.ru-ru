---
title: "Операторы пользовательской свертки в измерениях родители потомки | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bf4f123a7c2026fde28f9556957de20905330741
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>Атрибуты измерения родители потомки - операторы пользовательской свертки
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Операторы пользовательской свертки предоставляют простой способ управления способа свертки значений элементов в значения родительских элементов в иерархии родители потомки. В измерении, содержащем связь типа «родители-потомки», указывается столбец, содержащий унарные операторы, указывающие свертку для всех невычисляемых элементов родительского атрибута. Унарный оператор применяется к элементам каждый раз, когда оцениваются значения родительских элементов.  
  
 Унарные операторы хранятся в столбце, определенном свойством **UnaryOperatorColumn** родительского атрибута, и они применяются к каждому элементу атрибута. Столбец, заданный этим свойством, может находиться либо в таблице измерения, либо в таблице, связанной с таблицей измерения внешним ключом в таблице измерения.  
  
 Операторы пользовательской свертки предоставляют функционал, аналогичный, но более простой по сравнению с нестандартными формулами элементов. В нестандартной формуле элемента используются многомерные выражения для определения способа свертки элементов. В противоположность этому оператор пользовательской свертки использует простой унарный оператор для определения того, как значение элемента влияет на «родительский» элемент. Нестандартные формулы элементов предыдущего уровня имеют более высокий приоритет по сравнению с оператором пользовательской свертки уровня.  
  
## <a name="custom-rollup-precedence"></a>Приоритет пользовательской свертки  
 С точки зрения приоритетов, операторы пользовательской свертки атрибута источника для уровня в иерархии имеют более высокий приоритет, чем нестандартные формулы элементов предыдущего уровня. Однако нестандартные формулы элементов предыдущего уровня имеют более высокий приоритет, чем операторы пользовательской свертки уровня.  
  
## <a name="see-also"></a>См. также  
 [Определение нестандартных формул элементов](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [Унарные операторы в измерениях родители потомки](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
