---
title: Определение нового атрибута автоматически | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5368288930526435682723ba8f50d878ff029ce1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179622"
---
# <a name="attribute-properties---define-a-new-attribute-automatically"></a>Свойства атрибута — определение нового атрибута автоматически
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Новый атрибут измерения можно создать путем редактирования перетаскиванием элементов в конструкторе измерений.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Автоматическое создание нового атрибута  
  
1.  В конструкторе измерений откройте измерение, в котором необходимо создать атрибут.  
  
2.  На вкладке **Структура измерения** , на панели **Представление источника данных** , в таблице, к которой нужно привязать атрибут, выберите столбец и перетащите его в панель **Атрибуты** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают новый атрибут с тем же именем, что и у столбца, с которым он связан. Если к столбцу привязано несколько атрибутов, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляют номер к имени атрибута.  
  
## <a name="see-also"></a>См. также  
 [Измерения в многомерных моделях](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
