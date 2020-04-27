---
title: Фильтрация набора элементов в модели правил взаимосвязей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bef576a32bebc1c80b2ded8ee4831696811ba819
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084363"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Фильтрация набора элементов в модели ассоциативных правил
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]можно отфильтровать наборы элементов, отображаемые на вкладке **Наборы элементов** средства просмотра правил взаимосвязи ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ).  
  
### <a name="to-filter-an-itemset"></a>Фильтрация наборов элементов  
  
1.  На вкладке **Средство просмотра моделей интеллектуального анализа** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]перейдите на вкладку **Наборы элементов** в **Средство просмотра правил взаимосвязи**.  
  
2.  Введите условие правила в поле **Фильтрация набора элементов** . Например, условием правила может быть «Туризм-1000 = существующий»  
  
3.  Нажмите клавишу **ВВОД**.  
  
 Наборы элементов теперь отфильтрованы, чтобы отображать только те наборы, которые содержат выбранные элементы. Поле нечувствительно к регистру. Фильтры хранятся в памяти, чтобы из списка можно было выбрать старый фильтр.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции средства просмотра моделей интеллектуального анализа данных](mining-model-viewer-tasks-and-how-tos.md)  
  
  
