---
title: Просмотр или изменение параметров алгоритма | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58b512d726d45a8ceabb76a4ce2b1e6c8c62815b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209557"
---
# <a name="view-or-change-algorithm-parameters"></a>Просмотр или изменение параметров алгоритма
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Параметры алгоритма, используемого для построения моделей интеллектуального анализа данных, можно изменить для оптимизации результатов модели.  
  
 Параметры алгоритма, предоставляемые [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , изменяют не только свойства модели: их можно использовать для полного изменения способа обработки, группирования и отображения данных. Например, параметры алгоритма можно использовать для выполнения следующих операций.  
  
-   Изменение метода анализа, например метода кластеризации.  
  
-   Управление выбором компонентов.  
  
-   Указание размера наборов элементов или вероятности правил.  
  
-   Управление разветвлением и глубиной деревьев точности.  
  
-   Указание начального значения или размера внутренней перегрузки во время создания модели.  
  
 Сильно параметры, заданные для каждого алгоритма; список параметров, которые можно задать для каждого алгоритма см. в технических справочниках в этом разделе: [Алгоритмы интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
### <a name="change-an-algorithm-parameter"></a>Изменение параметров алгоритма  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]щелкните правой кнопкой мыши тип алгоритма модели интеллектуального анализа, для которого необходимо настроить алгоритм, и выберите **Задать параметры алгоритма**.  
  
     Откроется диалоговое окно **Параметры алгоритма** .  
  
2.  В столбце **Значение** задайте новое значение для алгоритма, который необходимо модифицировать.  
  
     Если значение в столбце **Значение** не введено, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют значение параметра по умолчанию. В столбце **Диапазон** указаны допустимые для ввода значения.  
  
3.  Нажмите кнопку **ОК**.  
  
     Параметру алгоритма присваивается новое значение. Изменение параметра не отразится на модели интеллектуального анализа данных до ее повторной обработки.  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a>Просмотр параметров существующей модели  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте окно DMX-запросов.  
  
2.  Введите примерно следующий запрос:  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
