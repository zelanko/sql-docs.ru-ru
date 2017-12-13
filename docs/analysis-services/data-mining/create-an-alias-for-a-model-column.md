---
title: "Создать псевдоним для столбца модели | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 579b9aedecce2df549e93459ccd368120d75ae3b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="create-an-alias-for-a-model-column"></a>создать псевдоним для столбца модели
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], можно создать псевдоним для столбца модели. Необходимость в этом может возникнуть, если имя структуры интеллектуального анализа данных имеет слишком большую длину и с ним неудобно работать, или если необходимо присвоить столбцу другое имя, более точно описывающее его содержимое или назначение в модели. Например, если создается копия столбца структуры, а затем дискретизация столбца выполняется различно для конкретной модели, можно переименовать столбец, чтобы его имя более точно отражало его содержимое.  
  
 Чтобы создать псевдоним для столбца модели, можно воспользоваться панелью **Свойства** и задать свойство [Name](../../analysis-services/scripting/properties/name-element-assl.md) столбца.  
  
 На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных псевдоним отображается в круглых скобках рядом с меткой использования столбца.  
  
 Дополнительные сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Добавление псевдонима к столбцу модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных щелкните правой кнопкой мыши ячейку в модели интеллектуального анализа данных для столбца интеллектуального анализа, которую необходимо изменить, и выберите пункт **Свойства**.  
  
2.  В окне **Свойства** в правой части экрана щелкните ячейку рядом со свойством Name и удалите текущее значение. Введите новое имя столбца.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Свойства модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-properties.md)  
  
  
