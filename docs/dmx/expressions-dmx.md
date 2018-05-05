---
title: Выражения (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: 1c9985c7bead076796201cedbf3189bc1dc1fe7a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="expressions-dmx"></a>Выражения (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 Чтобы построить составные выражения, можно комбинировать простые выражения с помощью операторов. Дополнительные сведения об операторах см. в разделе [расширений интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных & #40; расширений интеллектуального анализа данных & #41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных & #40; расширений интеллектуального анализа данных & #41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
