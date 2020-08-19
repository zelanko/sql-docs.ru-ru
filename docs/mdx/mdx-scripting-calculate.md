---
description: Инструкция CALCULATE (многомерные выражения)
title: Оператор CALCULATE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6ec4d0e86c2719613527ec7ea8206f980deebc3a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429766"
---
# <a name="mdx-scripting---calculate"></a>Сценарии многомерных выражений — CALCULATE


  Заполняет каждую ячейку куба статистическим значением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="remarks"></a>Remarks  
 Инструкция CALCULATE включается автоматически как первая в скрипте многомерного выражения куба, если куб создается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Эта инструкция статистически вычисляет каждую ячейку куба на основе ячеек с меньшей гранулярностью. Если после этого заполнить ячейки меньшей гранулярности значениями на основе выражений, это повлияет на значения ячеек большей гранулярности. Данная обработка выполняется практически всегда, но она может быть отменена или другие операторы могут быть выполнены раньше нее.  
  
 в скрипте многомерного выражения инструкция CALCULATE не может быть включена во вложенный подкуб. Вложенный подкуб определяется с помощью инструкции SCOPE. Дополнительные сведения об инструкции SCOPE см. в разделе [инструкция scope &#40;&#41;многомерных выражений ](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Вычисляемые элементы статистически не обрабатываются.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции скриптов многомерных выражений &#40;многомерные выражения&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Основные принципы создания скриптов многомерных выражений &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services)   
 [Определение назначений и других команд скриптов](https://docs.microsoft.com/analysis-services/multidimensional-models/define-assignments-and-other-script-commands)  
  
  
