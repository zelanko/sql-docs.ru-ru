---
title: "Операторы пользовательской свертки в измерениях родители потомки | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
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
ms.openlocfilehash: 1d731ba3666e4569a45b6ab3e9254a1eaafdda35
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>Атрибуты измерения родители потомки - операторы пользовательской свертки
  Операторы пользовательской свертки предоставляют простой способ контроля свертки значений элементов в значения родительских элементов в иерархии типа «родители-потомки». В измерении, содержащем связь типа «родители-потомки», указывается столбец, содержащий унарные операторы, указывающие свертку для всех невычисляемых элементов родительского атрибута. Унарный оператор применяется к элементам каждый раз, когда оцениваются значения родительских элементов.  
  
 Унарные операторы хранятся в столбце, определенном свойством **UnaryOperatorColumn** родительского атрибута, и они применяются к каждому элементу атрибута. Столбец, заданный этим свойством, может находиться либо в таблице измерения, либо в таблице, связанной с таблицей измерения внешним ключом в таблице измерения.  
  
 Операторы пользовательской свертки предоставляют функционал, аналогичный, но более простой по сравнению с нестандартными формулами элементов. В нестандартной формуле элемента используются многомерные выражения для определения способа свертки элементов. В противоположность этому оператор пользовательской свертки использует простой унарный оператор для определения того, как значение элемента влияет на «родительский» элемент. Нестандартные формулы элементов предыдущего уровня имеют более высокий приоритет по сравнению с оператором пользовательской свертки уровня.  
  
## <a name="custom-rollup-precedence"></a>Приоритет пользовательской свертки  
 С точки зрения приоритетов, операторы пользовательской свертки атрибута источника для уровня в иерархии имеют более высокий приоритет, чем нестандартные формулы элементов предыдущего уровня. Однако нестандартные формулы элементов предыдущего уровня имеют более высокий приоритет, чем операторы пользовательской свертки уровня.  
  
## <a name="see-also"></a>См. также  
 [Определение нестандартных формул элементов](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [Унарные операторы в измерениях родители потомки](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
