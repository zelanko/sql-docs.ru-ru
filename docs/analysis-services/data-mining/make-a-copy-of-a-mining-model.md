---
title: Создать копию модели интеллектуального анализа данных | Документы Microsoft
ms.custom: ''
ms.date: 03/20/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d63fecbd16ef15d13676f807558c56b094497317
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="make-a-copy-of-a-mining-model"></a>создать копию модели интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Создание копии модели интеллектуального анализа полезно, если необходимо быстро создать несколько моделей интеллектуального анализа данных на основе одних и тех же данных. После копирования модели новую копию можно редактировать путем изменения параметров или добавления фильтра.  
  
 Например, если существующая таблица Customers связана с таблицей данных о покупках, сделанных клиентами, можно создать отдельные модели интеллектуального анализа данных для каждого демографического показателя клиентов, такого как возраст или область.  
  
 Дополнительные сведения о копировании содержимого модели (например, географического представления или шаблонов модели) в буфер памяти для использования в другим программах см. в разделе [Копирование представления модели интеллектуального анализа данных](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md).  
  
### <a name="to-create-a-related-mining-model"></a>Создание связанной модели интеллектуального анализа данных  
  
1.  В обозревателе решений среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]щелкните структуру интеллектуального анализа данных, которая содержит модель интеллектуального анализа данных.  
  
2.  Перейдите на вкладку **Модели интеллектуального анализа данных** .  
  
3.  Выберите модель и щелкните правой кнопкой мыши, чтобы открыть контекстное меню.  
  
     –или–  
  
     Выберите модель. В меню **Модель интеллектуального анализа данных** выберите пункт **Новая модель интеллектуального анализа данных**.  
  
4.  Введите имя новой модели интеллектуального анализа данных и выберите алгоритм. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>Изменение фильтра в скопированной модели интеллектуального анализа данных  
  
1.  Выберите модель интеллектуального анализа данных.  
  
2.  В окне **Свойства** щелкните текстовое поле, относящееся к свойству **Фильтр** , а затем нажмите кнопку сборки **(...)** .  
  
3.  Измените условия фильтра.  
  
     Дополнительные сведения об использовании диалоговых окон редактора фильтров см. в разделе [Применение фильтра к модели интеллектуального анализа данных](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
4.  В окне **Свойства** в текстовом поле **AlgorithmParameters** нажмите кнопку **Задать параметры алгоритма**и, если необходимо, измените параметры алгоритма.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Фильтры для моделей интеллектуального анализа данных & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [Задачи модели интеллектуального анализа данных и инструкции](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Удалить фильтр из модели интеллектуального анализа данных](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  
