---
title: Определение нового атрибута автоматически | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d598ddb86e421309fe6aa7361595d64ddf1f0a24
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="attribute-properties---define-a-new-attribute-automatically"></a>Атрибут свойства - определение нового атрибута автоматически
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Новый атрибут измерения можно создать путем редактирования перетаскиванием элементов в конструкторе измерений.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Автоматическое создание нового атрибута  
  
1.  В конструкторе измерений откройте измерение, в котором необходимо создать атрибут.  
  
2.  На вкладке **Структура измерения** , на панели **Представление источника данных** , в таблице, к которой нужно привязать атрибут, выберите столбец и перетащите его в панель **Атрибуты** .  
  
     Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают новый атрибут с тем же именем, что и у столбца, с которым он связан. Если к столбцу привязано несколько атрибутов, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляют номер к имени атрибута.  
  
## <a name="see-also"></a>См. также  
 [Измерения в многомерных моделях](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
