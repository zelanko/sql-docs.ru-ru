---
title: ВЫЧИСЛИТЬ оператор (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 389c5f470cb3bf00cfe668a9405e36cd4ac8950e
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741943"
---
# <a name="mdx-scripting---calculate"></a>Скрипты многомерных Выражений: ВЫЧИСЛЕНИЯ


  Заполняет каждую ячейку куба статистическим значением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="remarks"></a>Примечания  
 Инструкция CALCULATE включается автоматически как первая в скрипте многомерного выражения куба, если куб создается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Эта инструкция статистически вычисляет каждую ячейку куба на основе ячеек с меньшей гранулярностью. Если после этого заполнить ячейки меньшей гранулярности значениями на основе выражений, это повлияет на значения ячеек большей гранулярности. Данная обработка выполняется практически всегда, но она может быть отменена или другие операторы могут быть выполнены раньше нее.  
  
 в скрипте многомерного выражения инструкция CALCULATE не может быть включена во вложенный подкуб. Вложенный подкуб определяется с помощью инструкции SCOPE. Дополнительные сведения об инструкции SCOPE см. в разделе [инструкции SCOPE &#40;многомерных Выражений&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Вычисляемые элементы статистически не обрабатываются.  
  
## <a name="see-also"></a>См. также  
 [Инструкции сценариев многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Основные понятия о сценариях многомерных Выражений &#40;служб Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Определение назначений и других команд скриптов](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
