---
title: Выражения (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0e1bd5fa1ba4d4ff8b97436ac6e44b901f578187
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074841"
---
# <a name="expressions-dmx"></a>Выражения (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  В расширениях интеллектуального анализа данных выражение представляет собой сочетание идентификаторов, значений и операторов, которые [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] могут вычислять результат.  
  
 Выражение расширений интеллектуального анализа данных может быть простым или составным. Простое выражение может быть одним из следующих:  
  
 Постоянно  
 Константа — это символ, представляющий одно конкретное значение. Константа может представлять собой строку, числовое значение или дату. Для ограничения констант типов строки и даты необходимо использовать одиночные кавычки (').  
  
 Скалярная функция  
 Скалярная функция возвращает одно значение.  
  
 Нескалярная функция  
 Нескалярная функция возвращает таблицу.  
  
 Идентификатор объекта  
 В расширениях интеллектуального анализа данных идентификаторы объектов считаются простыми выражениями.  
  
 Чтобы построить составные выражения, можно комбинировать простые выражения с помощью операторов. Дополнительные сведения об операторах см. в разделе [расширения интеллектуального анализа данных &#40;Справочник по операторам DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические обозначения&#41; DMX](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические&#41; DMX-элементы](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использование прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции расширения интеллектуального анализа данных SELECT](../dmx/understanding-the-dmx-select-statement.md)  
  
  
