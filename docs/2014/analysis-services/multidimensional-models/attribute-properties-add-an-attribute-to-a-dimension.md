---
title: Добавление атрибута в измерение | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b3f94d20f7f39efffd435793bf3dff808e115df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194844"
---
# <a name="add-an--attribute-to-a-dimension"></a>Добавление атрибута в измерение
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]добавлять атрибуты в измерение можно автоматически или вручную.  
  
 Чтобы создать атрибут автоматически, на вкладке **Структура измерения** конструктора измерений в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите столбец, который нужно сопоставить с атрибутом, и перетащите его с панели **Представление источника данных** на панель **Атрибуты** . Служба создаст сопоставленный столбцу атрибут, которому будет присвоено имя столбца. Если атрибут с таким именем уже существует, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляют к имени порядковый номер, начинающийся с 1 для первого повторяющегося имени.  
  
 Чтобы создать атрибут вручную, выберите режим просмотра панели **Attributes** в виде сетки. В столбце имени в последней строке сетки щелкните  **\<новый атрибут >** элемента. Введите имя нового атрибута. Будет создан атрибут, не сопоставленный столбцу, а всем свойствам атрибута будут присвоены значения по умолчанию. Атрибут можно сопоставить столбцу в окне **Свойства** среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , настроив свойство **KeyColumns** нового атрибута.  
  
 Дополнительные сведения см. в разделах [Определение нового атрибута автоматически](attribute-properties-define-a-new-attribute-automatically.md), [Определение нового атрибута вручную](../define-a-new-attribute-manually.md), [Привязка атрибута к столбцу имени](attribute-properties-bind-an-attribute-to-a-name-column.md)и [Изменение свойства KeyColumn атрибута](attribute-properties-modify-the-keycolumn-property.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по свойствам атрибута измерения](dimension-attribute-properties-reference.md)  
  
  