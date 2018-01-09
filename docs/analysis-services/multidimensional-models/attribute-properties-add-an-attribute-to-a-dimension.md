---
title: "Добавление атрибута в измерение | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d5f620f394ab70b0fea579875c23e7f0eb8716db
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="attribute-properties---add-an--attribute-to-a-dimension"></a>Атрибут свойства — Добавление атрибута в измерение
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Добавлять атрибута в измерение можно автоматически или вручную в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Чтобы создать атрибут автоматически, на вкладке **Структура измерения** конструктора измерений в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите столбец, который нужно сопоставить с атрибутом, и перетащите его с панели **Представление источника данных** на панель **Атрибуты** . Служба создаст сопоставленный столбцу атрибут, которому будет присвоено имя столбца. Если атрибут с таким именем уже существует, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляют к имени порядковый номер, начинающийся с 1 для первого повторяющегося имени.  
  
 Чтобы создать атрибут вручную, выберите режим просмотра панели **Attributes** в виде сетки. В столбце имени в последней строке сетки щелкните  **\<новый атрибут >** элемента. Введите имя нового атрибута. Будет создан атрибут, не сопоставленный столбцу, а всем свойствам атрибута будут присвоены значения по умолчанию. Атрибут можно сопоставить столбцу в окне **Свойства** среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , настроив свойство **KeyColumns** нового атрибута.  
  
 Дополнительные сведения см. в разделах [Определение нового атрибута автоматически](../../analysis-services/multidimensional-models/attribute-properties-define-a-new-attribute-automatically.md), [Привязка атрибута к столбцу имени](../../analysis-services/multidimensional-models/attribute-properties-bind-an-attribute-to-a-name-column.md)и [Изменение свойства KeyColumn атрибута](../../analysis-services/multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)добавлять атрибуты в измерение можно автоматически или вручную.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
