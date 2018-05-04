---
title: ВЫЧИСЛИТЬ оператор (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CALCULATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CALCULATE statement
ms.assetid: 41e196a1-d49e-487b-a42a-73e5d441ed1b
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 9be6ad404ade5784ab86845b90cda51b2b939bdf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-scripting---calculate"></a>Скрипты многомерных Выражений: ВЫЧИСЛЕНИЯ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Заполняет каждую ячейку куба статистическим значением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Аргументы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Инструкция CALCULATE включается автоматически как первая в скрипте многомерного выражения куба, если куб создается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Эта инструкция статистически вычисляет каждую ячейку куба на основе ячеек с меньшей гранулярностью. Если после этого заполнить ячейки меньшей гранулярности значениями на основе выражений, это повлияет на значения ячеек большей гранулярности. Данная обработка выполняется практически всегда, но она может быть отменена или другие операторы могут быть выполнены раньше нее.  
  
 в скрипте многомерного выражения инструкция CALCULATE не может быть включена во вложенный подкуб. Вложенный подкуб определяется с помощью инструкции SCOPE. Дополнительные сведения об инструкции SCOPE см. в разделе [инструкции SCOPE &#40;многомерных Выражений&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Вычисляемые элементы статистически не обрабатываются.  
  
## <a name="see-also"></a>См. также  
 [Инструкции сценариев многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Основные понятия о сценариях многомерных Выражений & #40; Службы Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Определение назначений и других команд скриптов](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
