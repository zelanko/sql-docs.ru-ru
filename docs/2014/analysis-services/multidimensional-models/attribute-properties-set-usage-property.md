---
title: Установка свойства использования | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], usage setting
- usage options [Analysis Services]
ms.assetid: 7b0ebc58-94b9-4523-8994-e7bc796b0bd8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f2ab9f98018e421bd14012af7d8bd1cb5da3a71c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62701702"
---
# <a name="set-usage-property"></a>Установка свойства использования
  Можно задать использование атрибута с помощью представления **Структура измерения** в конструкторе измерений, доступ к которому выполняется из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 При задании использования атрибута изменения вступают в силу только после обработки измерения. Дополнительные сведения см. в разделе [обработку объекта многомерных моделей](processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-set-usage-for-an-attribute"></a>Задание использования атрибута  
  
1.  В обозревателе решений щелкните правой кнопкой мыши измерение и выберите пункт **Открыть**.  
  
     По умолчанию откроется представление **Структура измерения** .  
  
2.  В списке **Атрибуты**щелкните правой кнопкой мыши атрибут, для которого требуется задать использование, и выберите пункт **Задать использование атрибута**, а затем установите один из следующих флажков:  
  
    -   **Regular**  
  
    -   **Key**  
  
    -   **Parent**  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Добавление атрибута в измерение](attribute-properties-add-an-attribute-to-a-dimension.md)  
  
  
