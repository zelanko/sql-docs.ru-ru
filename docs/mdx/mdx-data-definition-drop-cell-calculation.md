---
title: Инструкция DROP CELL CALCULATION (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac37584d12f2efa68084ada626ba57ab9fb28155
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579316"
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>Определения данных многомерных Выражений — DROP CELL CALCULATION
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Удаляет указанное вычисление ячейки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP [ SESSION ] CELL CALCULATION CURRENTCUBE | Cube_Name.CellCalc_Name  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, представляющее имя выражения куба.  
  
 *CellCalc_Name*  
 Допустимое строковое выражение, возвращающее имя вычисления ячейки, которое необходимо удалить.  
  
## <a name="see-also"></a>См. также  
 [Инструкция CREATE CELL CALCULATION &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
