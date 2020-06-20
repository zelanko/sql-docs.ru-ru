---
title: Преобразование "Запрос интеллектуального анализа данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 10a8c6495fc7d839132d102d9e696263a6f9df17
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939635"
---
# <a name="data-mining-query-transformation"></a>преобразование «Запрос интеллектуального анализа данных»
  Преобразование «Запрос интеллектуального анализа данных» выполняет прогнозирующие запросы на основе моделей интеллектуального анализа данных. Это преобразование содержит построитель запросов для создания запросов расширений интеллектуального анализа данных (DMX). С помощью построителя запросов можно создавать пользовательские инструкции на языке расширения интеллектуального анализа данных (DMX) для оценки входа преобразования в соответствии с текущей моделью интеллектуального анализа данных. Дополнительные сведения см. в разделе [Справочник по расширениям интеллектуального анализа данных](/sql/dmx/data-mining-extensions-dmx-reference).  
  
 Одно преобразование может выполнять несколько прогнозирующих запросов, если их модели созданы на основе одной и той же структуры интеллектуального анализа данных. Дополнительные сведения см. в разделе [интерфейсы запросов интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>Настройка преобразования «Запрос интеллектуального анализа данных»  
 Преобразование «Запрос интеллектуального анализа данных» использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , чтобы подключить проект служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , содержащие структуры и модели интеллектуального анализа данных. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md).  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно настроить при помощи диалогового окна **Редактор преобразования «Запрос интеллектуального анализа данных»** , см. в следующих разделах:  
  
-   [Редактор преобразования "Запрос интеллектуального анализа данных" (вкладка "Модель интеллектуального анализа данных")](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [Редактор преобразования "Запрос интеллектуального анализа данных" (вкладка "Модель интеллектуального анализа данных")](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Transformation Custom Properties](transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
  
