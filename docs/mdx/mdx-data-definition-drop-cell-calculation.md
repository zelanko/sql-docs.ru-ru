---
title: "Инструкция DROP CELL CALCULATION (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Calculation
- DROP
- DROP_CELL_CALCULATION
- CELL CALCULATION
- DROP CELL
- cell
- DROP CELL CALCULATION
dev_langs: kbMDX
helpviewer_keywords:
- deleting calculations
- dropping calculations
- removing calculations
- DROP CELL CALCULATION statement
- calculations [SQL Server]
- cubes [Analysis Services], calculations
ms.assetid: 77caedf4-dd96-4eac-a5e4-fd82148a44a7
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3b6eb5761f8f9036c4585b4ac81860f676759388
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>Определения данных многомерных Выражений — DROP CELL CALCULATION
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Создать инструкции ВЫЧИСЛЕНИЯ ЯЧЕЙКИ &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Инструкции определения данных &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
