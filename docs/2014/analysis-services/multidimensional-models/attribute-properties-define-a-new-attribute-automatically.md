---
title: Определение нового атрибута автоматически | Документы Microsoft
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
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 007f736d3e14a4e8ac2d2b1446819b72a3443fbd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179956"
---
# <a name="define-a-new-attribute-automatically"></a>Определение нового атрибута автоматически
  Новый атрибут измерения можно создать путем редактирования перетаскиванием элементов в конструкторе измерений.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Автоматическое создание нового атрибута  
  
1.  В конструкторе измерений откройте измерение, в котором необходимо создать атрибут.  
  
2.  На вкладке **Структура измерения** , на панели **Представление источника данных** , в таблице, к которой нужно привязать атрибут, выберите столбец и перетащите его в панель **Атрибуты** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают новый атрибут с тем же именем, что и у столбца, с которым он связан. Если к столбцу привязано несколько атрибутов, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляют номер к имени атрибута.  
  
## <a name="see-also"></a>См. также  
 [Измерения в многомерных моделях](dimensions-in-multidimensional-models.md)   
 [Справочник по свойствам атрибута измерения](dimension-attribute-properties-reference.md)  
  
  