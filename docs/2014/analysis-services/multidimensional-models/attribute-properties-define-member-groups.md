---
title: Определение групп элементов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 389439143ddd5f56d565cdebff42a91e241e16fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219344"
---
# <a name="define-member-groups"></a>Определение групп элементов
  Если атрибут содержит большое число элементов, можно сгруппировать их в контейнеры, уменьшая таким образом число элементов, которые будут видеть пользователи при просмотре иерархии данных. Также можно задать число контейнеров, по которым будут группироваться контейнеры, и установить схему именования контейнеров. Дополнительные сведения см. в разделе [Группирование элементов атрибутов (дискретизация)](attribute-properties-group-attribute-members.md).  
  
 Элементы группируются путем установки свойства **DiscretizationMethod** , доступ к которому можно получить с помощью окна **Свойства** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Когда создаются группы элементов, изменения не будут доступны пользователям до обработки измерения. Дополнительные сведения см. в разделе [обработку объекта многомерных моделей](processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Создание групп элементов  
  
1.  Откройте измерение, необходимое для работы. По умолчанию откроется вкладка **Структура измерения** .  
  
2.  В окне **Атрибуты**щелкните правой кнопкой мыши атрибут, элементы которого нужно сгруппировать, а затем выберите пункт **Свойства**.  
  
3.  В раскрывающемся списке рядом с полем **DiscretizationMethod** выберите метод группирования элементов. Дополнительные сведения о настройках **DiscretizationMethod** см. в разделе [Группирование элементов атрибутов (дискретизация)](attribute-properties-group-attribute-members.md).  
  
  
