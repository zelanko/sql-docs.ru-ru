---
title: Определение нового атрибута автоматически | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 10c0a014cb83b8384fd7d742073140eb0e018237
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171294"
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
  
  
