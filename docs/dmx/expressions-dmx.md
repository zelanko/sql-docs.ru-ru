---
title: "Выражения (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], expressions
- DMX [Analysis Services], expressions
- expressions [DMX]
ms.assetid: 00579552-19c8-4e9d-a790-f88df3e1aeea
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c04c55fc461d4429d55d32a776f5bea8eca345e8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="expressions-dmx"></a>Выражения (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В расширений интеллектуального анализа (DMX), выражение представляет собой сочетание идентификаторов, значений и операторов, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] можно вычислить для получения результата.  
  
 Выражение расширений интеллектуального анализа данных может быть простым или составным. Простое выражение может быть одним из следующих:  
  
 Константа  
 Константа — это символ, представляющий одно конкретное значение. Константа может представлять собой строку, числовое значение или дату. Для ограничения констант типов строки и даты необходимо использовать одиночные кавычки (').  
  
 Скалярная функция  
 Скалярная функция возвращает одно значение.  
  
 Нескалярная функция  
 Нескалярная функция возвращает таблицу.  
  
 Идентификатор объекта  
 В расширениях интеллектуального анализа данных идентификаторы объектов считаются простыми выражениями.  
  
 Чтобы построить составные выражения, можно комбинировать простые выражения с помощью операторов. Дополнительные сведения об операторах см. в разделе [расширений интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Основные сведения об инструкции расширений интеллектуального анализа данных Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  

