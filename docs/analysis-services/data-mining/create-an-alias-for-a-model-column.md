---
title: "Создать псевдоним для столбца модели | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a49c5aac7289573631a3ed50349c98690c28212d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-an-alias-for-a-model-column"></a>создать псевдоним для столбца модели
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]для столбца модели можно создать псевдоним. Необходимость в этом может возникнуть, если имя структуры интеллектуального анализа данных имеет слишком большую длину и с ним неудобно работать, или если необходимо присвоить столбцу другое имя, более точно описывающее его содержимое или назначение в модели. Например, если создается копия столбца структуры, а затем дискретизация столбца выполняется различно для конкретной модели, можно переименовать столбец, чтобы его имя более точно отражало его содержимое.  
  
 Чтобы создать псевдоним для столбца модели, можно воспользоваться панелью **Свойства** и задать свойство [Name](../../analysis-services/scripting/properties/name-element-assl.md) столбца.  
  
 На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных псевдоним отображается в круглых скобках рядом с меткой использования столбца.  
  
 Дополнительные сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Добавление псевдонима к столбцу модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных щелкните правой кнопкой мыши ячейку в модели интеллектуального анализа данных для столбца интеллектуального анализа, которую необходимо изменить, и выберите пункт **Свойства**.  
  
2.  В окне **Свойства** в правой части экрана щелкните ячейку рядом со свойством Name и удалите текущее значение. Введите новое имя столбца.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Свойства модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-properties.md)  
  
  

