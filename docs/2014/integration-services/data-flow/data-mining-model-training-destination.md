---
title: Назначение "Обучение модели интеллектуального анализа данных" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5dac84fe42185806ae468593876a6bd439c1c689
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68890647"
---
# <a name="data-mining-model-training-destination"></a>целевой объект «Обучение модели интеллектуального анализа данных»
  Целевой объект «Обучение модели интеллектуального анализа данных» обучает модели анализа данных, пропуская данные, которые получает целевой объект, через алгоритмы модели интеллектуального анализа данных. Несколько моделей интеллектуального анализа данных могут быть обучены одним целевым объектом, если модели построены на одной и той же структуре интеллектуального анализа данных. Дополнительные сведения см. в разделах [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) и [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a>Настройка назначения «Обучение модели интеллектуального анализа данных».  
 Если столбец уровня вариантов в целевой структуре и модели построены на структуре, содержимое которой типа KEY TIME или KEY SEQUENCE, входные данные должны быть отсортированы по этой колонке. Например, модели, созданные с использованием алгоритма временных рядов (Майкрософт), используют тип содержимого KEY TIME. Если входные данные не отсортированы, то обработка модели может завершиться неудачно. Если данные требуется отсортировать, можно в потоке данных предварительно использовать преобразование «Сортировка» для их сортировки. Это требование не относится к столбцам с типом содержимого KEY. Дополнительные сведения см. в разделе [Типы содержимого (интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) и [Преобразование "Сортировка"](transformations/sort-transformation.md).  
  
> [!NOTE]  
>  Входные данные целевого объекта «Обучение модели интеллектуального анализа данных» должны быть отсортированы. Чтобы отсортировать данные, следует включить целевой объект «Сортировка» в поток данных к назначению «Обучение модели интеллектуального анализа данных». Дополнительные сведения см. в разделе [Sort Transformation](transformations/sort-transformation.md).  
  
 Этот целевой объект имеет один вход и ни одного выхода.  
  
 Назначение «обучение модели интеллектуального анализа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » использует диспетчер соединений для подключения [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] к проекту или к экземпляру [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащему структуру и модели интеллектуального анализа данных, которые обучены в целевом объекте. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые могут быть заданы в диалоговом окне **Редактор сценариев обучения моделей интеллектуального анализа данных** , см. в одном из следующих разделов:  
  
-   [Редактор обучения моделей интеллектуального анализа данных &#40;вкладка "подключение"&#41;](../data-mining-model-training-editor-connection-tab.md)  
  
-   [Редактор обучения моделей интеллектуального анализа данных &#40;вкладка "столбцы"&#41;](../data-mining-model-training-editor-columns-tab.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../common-properties.md)  
  
-   [Пользовательские свойства назначения «Обучение модели интеллектуального анализа данных»](data-mining-model-training-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
  
