---
title: "Просмотр и сохранение результатов прогнозирующего запроса | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c930bb5890fe78d46da5d8711ffbdcfb43c7e36a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a>Просмотр и сохранение результатов прогнозирующего запроса
  После создания запроса в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью построителя прогнозирующих запросов, можно выполнить этот запрос и просмотреть результат, переключившись в представление результатов запроса.  
  
 Можно сохранить результаты прогнозирующего запроса в таблице в любом источнике данных, определенном в проекте служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Можно либо создать новую таблицу, либо сохранить результаты запроса в существующую таблицу. При сохранении результатов в существующую таблицу можно выбрать перезапись данных, хранящихся в таблице в текущий момент, в противном случае результаты будут добавлены к существующим данным в таблице.  
  
### <a name="run-a-query-and-view-the-results"></a>Выполните запрос и просмотрите результаты  
  
1.  На панели инструментов вкладки **Прогнозирование моделей интеллектуального анализа** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]нажмите кнопку **Результат** .  
  
     Откроется окно результатов и выполнится запрос. Результаты отображаются в сетке в средстве просмотра.  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a>Cохраните результаты прогнозирующего запроса в таблицу  
  
1.  На панели инструментов вкладки **Прогнозирование моделей интеллектуального анализа данных** в конструкторе интеллектуального анализа данных нажмите кнопку **Сохранить результат запроса**.  
  
     Откроется диалоговое окно **Сохранение результата запроса интеллектуального анализа данных** .  
  
2.  Выберите источник данных из списка **Источник данных** или нажмите кнопку **Создать** , чтобы создать новый источник данных.  
  
3.  В поле **Имя таблицы** введите имя таблицы. Если таблица уже существует, то установите флажок **Перезаписать при существовании** , чтобы заменить содержимое таблицы результатами запроса. Если не нужно перезаписывать содержимое таблицы, то не устанавливайте этот флажок. Результаты нового запроса будут добавлены к существующим данным в таблице.  
  
4.  Выберите представление источника данных из списка **Добавить к представлению источника данных** , если необходимо добавить таблицу к представлению источника данных.  
  
5.  Нажмите кнопку **Сохранить**.  
  
    > [!WARNING]  
    >  Если место назначения не поддерживает иерархические наборы строк, можно добавить в результаты ключевое слово FALTTENED для сохранения результатов в виде плоской таблицы.  
  
  
