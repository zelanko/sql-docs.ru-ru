---
title: Оператор DROP для вычисления ЯЧЕЙКИ (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bccdd6efcf17af9d485e155b6653bab52bbcbd3b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038226"
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>Определение данных многомерных выражений — DROP CELL CALCULATION


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
  
## <a name="see-also"></a>См. также:  
 [СОЗДАНИЕ инструкции вычисления ЯЧЕЙКИ &#40;многомерных выражениях&#41;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
