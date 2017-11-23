---
title: "Удалить фильтр из модели интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 36eec0622aa30b2ece9eac7ff3ee3b4e6403d252
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="delete-a-filter-from-a-mining-model"></a>удалить фильтр из модели интеллектуального анализа данных
  При создании фильтра для модели интеллектуального анализа можно создавать модели для подмножества данных в представлении источника данных. Фильтры также полезны при тестировании точности модели на подмножестве исходных данных.  
  
 Однако если потребуется снова рассмотреть полное множество вариантов, необходимо будет удалить этот фильтр. Эта процедура описывает удаление условий фильтра и фильтра полностью.  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>Удаление условия фильтра модели интеллектуального анализа данных  
  
1.  В обозревателе решений [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]щелкните структуру интеллектуального анализа данных, содержащую ту модель интеллектуального анализа данных, к которой нужно применить фильтр.  
  
2.  Перейдите на вкладку **Модели интеллектуального анализа данных** .  
  
3.  Выберите модель и щелкните правой кнопкой мыши, чтобы открыть контекстное меню.  
  
     –или–  
  
     Выберите модель. В меню **Модель интеллектуального анализа данных** выберите команду **Установить фильтр моделей**.  
  
4.  В диалоговом окне **Фильтр модели** щелкните правой кнопкой строку в сетке, которая содержит условие, которое необходимо удалить.  
  
5.  Выберите команду **Удалить**.  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>Очистка фильтра модели интеллектуального анализа данных в диалоговом окне «Редактор фильтров»  
  
-   В диалоговом окне **Редактор фильтров** щелкните правой кнопкой мыши любую строку в сетке и выберите команду **Удалить все**.  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>Работа с фильтрами моделей с помощью окна «Свойства»  
 Если нужно удалить весь фильтр, нет необходимости открывать диалоговые окна редактора фильтра. Созданные условия фильтра доступны в свойстве **Filter** модели интеллектуального анализа данных.  
  
> [!NOTE]  
>  Свойства модели интеллектуального анализа данных можно просматривать в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], но не в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>Очистка фильтра модели интеллектуального анализа данных в обозревателе решений  
  
1.  В обозревателе решений щелкните модель интеллектуального анализа данных, содержащую фильтр.  
  
2.  В окне **Свойства** щелкните правой кнопкой текст фильтра в свойстве **Фильтр** и выберите команду **Выделить все**.  
  
3.  Нажмите клавишу "BACKSPACE" или "DELETE".  
  
## <a name="see-also"></a>См. также  
 [выполнить детализацию до данных вариантов из модели интеллектуального анализа данных](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
