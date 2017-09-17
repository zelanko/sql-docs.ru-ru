---
title: "Фильтр набора элементов в ассоциации модели правил | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 785aac0e04863365210d3f1da9e850331f8e782f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Фильтрация набора элементов в модели ассоциативных правил
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]можно отфильтровать наборы элементов, отображаемые на вкладке **Наборы элементов** средства просмотра правил взаимосвязи ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ).  
  
### <a name="to-filter-an-itemset"></a>Фильтрация наборов элементов  
  
1.  На вкладке **Средство просмотра моделей интеллектуального анализа** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]перейдите на вкладку **Наборы элементов** в **Средство просмотра правил взаимосвязи**.  
  
2.  Введите условие правила в поле **Фильтрация набора элементов** . Например, условием правила может быть «Туризм-1000 = существующий»  
  
3.  Нажмите клавишу **ВВОД**.  
  
 Наборы элементов теперь отфильтрованы, чтобы отображать только те наборы, которые содержат выбранные элементы. Поле нечувствительно к регистру. Фильтры хранятся в памяти, чтобы из списка можно было выбрать старый фильтр.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции средства просмотра моделей интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
