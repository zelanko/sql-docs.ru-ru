---
title: "Инструкция DROP KPI (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KPI
- DROP
- DROP KPI
- DROP_KPI
helpviewer_keywords:
- DROP KPI statement
- key performance indicators [MDX]
ms.assetid: d19c6809-b8a6-459d-8554-b41854f7cc45
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 656ca9db230c52c77ce7be612ed8dcc78ade3bf8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---drop-kpi"></a>Определения данных многомерных Выражений — DROP KPI
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет указанный ключевой показатель эффективности из заданного куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP KPI CURRENTCUBE | Cube_Name.KPI_Name   
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимая строка, указывающая имя куба.  
  
 *KPI_Name*  
 Допустимое строковое выражение, указывающее имя ключевого показателя эффективности, который должен быть удален.  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ KPI, инструкция &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-kpi.md)   
 [Инструкции определения данных &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
