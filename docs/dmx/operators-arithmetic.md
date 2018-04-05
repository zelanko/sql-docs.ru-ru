---
title: Арифметические операторы (расширения интеллектуального анализа данных) | Документы Microsoft
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
- arithmetic operators
ms.assetid: befe4f0c-e5dd-4ae1-b88e-6ac7aab2181a
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c256882453ca3536a21babb2d87b774e9aab3d6d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="operators---arithmetic"></a>Операторы — арифметические операции
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Арифметические операторы можно использовать в расширений интеллектуального анализа (DMX) для арифметических вычислений в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], в том числе сложения, вычитания, умножения и деления.  
  
 В следующей таблице даны арифметические операторы, поддерживаемые расширениями интеллектуального анализа данных.  
  
|Оператор|Description|  
|--------------|-----------------|  
|[+ &#40; Добавить &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/add-dmx.md)|Складывает два числа.|  
|[-&#40; Вычитание &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/subtract-dmx.md)|Вычитает одно число из другого.|  
|[&#42; &#40; Умножьте &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/multiply-dmx.md)|Умножает одно число на другое.|  
|[&#40; деления &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/divide-dmx.md)|Делит одно число на другое.|  
  
 Следующие правила определяют очередность выполнения арифметических операторов в выражении расширений интеллектуального анализа данных:  
  
-   Если в выражении присутствует несколько арифметических операторов, умножение и деление выполняются в первую очередь, затем — вычитание и сложение.  
  
-   Если все арифметические операторы в выражении имеют одинаковую очередность, они выполняются слева направо.  
  
-   Выражения, находящиеся внутри скобок, имеют наибольший приоритет.  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Выражения &#40; расширений интеллектуального анализа данных &#41;](../dmx/expressions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-dmx.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
