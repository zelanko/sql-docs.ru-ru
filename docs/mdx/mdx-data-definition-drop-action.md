---
title: "Инструкция DROP ACTION (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP
- DROP ACTION
- Action
- DROP_ACTION
dev_langs: kbMDX
helpviewer_keywords:
- DROP ACTION statement
- deleting actions
- removing actions
- actions [MDX]
- dropping actions
ms.assetid: 74b3cfee-dea8-4968-a54c-1754d52ee1bd
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 22233dcfb79c9e2cf86e0c9fd7168ae321ed2034
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---drop-action"></a>Определение данных MDX - действия удаления
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет указанное действие из указанного куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP ACTION CURRENTCUBE | Cube_Name  
   .Action_Name   
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, возвращающее имя куба.  
  
 *Имя_действия*  
 Допустимое строковое выражение, возвращающее имя действия, которое необходимо удалить.  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ оператор действия &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-action.md)   
 [Инструкции определения данных &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
