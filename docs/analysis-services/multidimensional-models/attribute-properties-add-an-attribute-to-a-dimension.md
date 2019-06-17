---
title: Добавление атрибута в измерение | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02773eadf282fe9ac25fa96543a86c5d3e77da4c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63020614"
---
# <a name="attribute-properties---add-an--attribute-to-a-dimension"></a>Свойства атрибута — добавление атрибута в измерение
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]добавлять атрибуты в измерение можно автоматически или вручную.  
  
 Чтобы создать атрибут автоматически, на вкладке **Структура измерения** конструктора измерений в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите столбец, который нужно сопоставить с атрибутом, и перетащите его с панели **Представление источника данных** на панель **Атрибуты** . Служба создаст сопоставленный столбцу атрибут, которому будет присвоено имя столбца. Если атрибут с таким именем уже существует, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляют к имени порядковый номер, начинающийся с 1 для первого повторяющегося имени.  
  
 Чтобы создать атрибут вручную, выберите режим просмотра панели **Attributes** в виде сетки. В столбце имени в последней строке сетки щелкните  **\<новый атрибут >** элемента. Введите имя нового атрибута. Будет создан атрибут, не сопоставленный столбцу, а всем свойствам атрибута будут присвоены значения по умолчанию. Атрибут можно сопоставить столбцу в окне **Свойства** среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , настроив свойство **KeyColumns** нового атрибута.  
  
 Дополнительные сведения см. в разделах [Определение нового атрибута автоматически](../../analysis-services/multidimensional-models/attribute-properties-define-a-new-attribute-automatically.md), [Привязка атрибута к столбцу имени](../../analysis-services/multidimensional-models/attribute-properties-bind-an-attribute-to-a-name-column.md)и [Изменение свойства KeyColumn атрибута](../../analysis-services/multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)добавлять атрибуты в измерение можно автоматически или вручную.  
  
## <a name="see-also"></a>См. также  
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
