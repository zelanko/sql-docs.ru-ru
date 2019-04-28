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
ms.openlocfilehash: 9d00be2992f9ad661736f65e4d1146a34fe1fad0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827975"
---
# <a name="data-mining-model-training-destination"></a>целевой объект «Обучение модели интеллектуального анализа данных»
  Целевой объект «Обучение модели интеллектуального анализа данных» обучает модели анализа данных, пропуская данные, которые получает целевой объект, через алгоритмы модели интеллектуального анализа данных. Несколько моделей интеллектуального анализа данных могут быть обучены одним целевым объектом, если модели построены на одной и той же структуре интеллектуального анализа данных. Дополнительные сведения см. в разделах [Mining Structure Columns](../../analysis-services/data-mining/mining-structure-columns.md) и [Mining Model Columns](../../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a>Настройка назначения «Обучение модели интеллектуального анализа данных».  
 Если столбец уровня вариантов в целевой структуре и модели построены на структуре, содержимое которой типа KEY TIME или KEY SEQUENCE, входные данные должны быть отсортированы по этой колонке. Например, модели, созданные с использованием алгоритма временных рядов (Майкрософт), используют тип содержимого KEY TIME. Если входные данные не отсортированы, то обработка модели может завершиться неудачно. Если данные требуется отсортировать, можно в потоке данных предварительно использовать преобразование «Сортировка» для их сортировки. Это требование не относится к столбцам с типом содержимого KEY. Дополнительные сведения см. в разделе [Типы содержимого (интеллектуальный анализ данных)](../../analysis-services/data-mining/content-types-data-mining.md) и [Преобразование "Сортировка"](transformations/sort-transformation.md).  
  
> [!NOTE]  
>  Входные данные целевого объекта «Обучение модели интеллектуального анализа данных» должны быть отсортированы. Чтобы отсортировать данные, следует включить целевой объект «Сортировка» в поток данных к назначению «Обучение модели интеллектуального анализа данных». Дополнительные сведения см. в статье [Sort Transformation](transformations/sort-transformation.md).  
  
 Этот целевой объект имеет один вход и ни одного выхода.  
  
 Назначение «Обучение модели интеллектуального анализа данных» использует диспетчер соединений служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для подключения к проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащему структуру интеллектуального анализа данных и модели интеллектуального анализа, которые обучаются с помощью назначения. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые могут быть заданы в диалоговом окне **Редактор сценариев обучения моделей интеллектуального анализа данных** , см. в одном из следующих разделов:  
  
-   [Редактор обучения модели интеллектуального анализа данных (вкладка "Соединение")](../data-mining-model-training-editor-connection-tab.md)  
  
-   [Редактор обучения модели интеллектуального анализа данных (вкладка "Столбцы")](../data-mining-model-training-editor-columns-tab.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../common-properties.md)  
  
-   [Пользовательские свойства назначения «Обучение модели интеллектуального анализа данных»](data-mining-model-training-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
  
