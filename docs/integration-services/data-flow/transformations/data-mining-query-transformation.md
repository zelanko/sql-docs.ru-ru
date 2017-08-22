---
title: "Интеллектуальный анализ данных преобразование «запрос» | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 544f0aaf11e83b9ba2fc0ae5150b85e537998c25
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="data-mining-query-transformation"></a>преобразование «Запрос интеллектуального анализа данных»
  Преобразование «Запрос интеллектуального анализа данных» выполняет прогнозирующие запросы на основе моделей интеллектуального анализа данных. Это преобразование содержит построитель запросов для создания запросов расширений интеллектуального анализа данных (DMX). С помощью построителя запросов можно создавать пользовательские инструкции на языке расширения интеллектуального анализа данных (DMX) для оценки входа преобразования в соответствии с текущей моделью интеллектуального анализа данных. Дополнительные сведения см. в разделе [Справочник по расширениям интеллектуального анализа данных](../../../dmx/data-mining-extensions-dmx-reference.md).  
  
 Одно преобразование может выполнять несколько прогнозирующих запросов, если их модели созданы на основе одной и той же структуры интеллектуального анализа данных. Дополнительные сведения см. в статье [Средства запросов интеллектуального анализа данных](../../../analysis-services/data-mining/data-mining-query-tools.md).  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>Настройка преобразования «Запрос интеллектуального анализа данных»  
 Преобразование «Запрос интеллектуального анализа данных» использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , чтобы подключить проект служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , содержащие структуры и модели интеллектуального анализа данных. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно настроить при помощи диалогового окна **Редактор преобразования «Запрос интеллектуального анализа данных»** , см. в следующих разделах:  
  
-   [Редактор преобразования "Запрос интеллектуального анализа данных" (вкладка "Модель интеллектуального анализа данных")](../../../integration-services/data-flow/transformations/data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [Редактор преобразования "Запрос интеллектуального анализа данных" (вкладка "Модель интеллектуального анализа данных")](../../../integration-services/data-flow/transformations/data-mining-query-transformation-editor-mining-model-tab.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
