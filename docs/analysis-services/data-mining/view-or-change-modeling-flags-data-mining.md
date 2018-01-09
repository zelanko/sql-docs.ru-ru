---
title: "Просмотр или изменение флагов модели (интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0109b4a95a81536cee4b00a5b4da05697219f769
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="view-or-change-modeling-flags-data-mining"></a>Просмотр или изменение флагов модели (интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Флаги модели представляют собой свойства, установленные для структуры интеллектуального анализа данных столбец или столбцы модели интеллектуального анализа данных для управления, как алгоритм обрабатывает данные во время анализа.  
  
 В конструкторе моделей интеллектуального анализа данных можно просматривать и изменять флаги модели, связанные со структурой интеллектуального анализа данных или столбцом интеллектуального анализа, рассматривая свойства структуры или модели. Флаги моделирования также можно задавать с помощью DMX, AMO или XMLA.  
  
 В этой процедуре описывается, как изменять флаги моделирования в конструкторе.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>Просмотр или изменение флага моделирования для столбца структуры или столбца модели  
  
1.  В среде SQL Server Design Studio откройте обозреватель решений и дважды щелкните структуру интеллектуального анализа данных.  
  
2.  Чтобы задать флаг модели NOT NULL, откройте вкладку **Структура интеллектуального анализа данных** . Чтобы задать флаги REGRESSOR или MODEL_EXISTENCE_ONLY, откройте вкладку **Модель интеллектуального анализа данных** .  
  
3.  Щелкните правой кнопкой мыши столбец, который необходимо просмотреть или изменить, и выберите команду **Свойства**.  
  
4.  Чтобы добавить новый флаг модели, щелкните текстовое поле рядом со свойством **ModelingFlags** и отметьте один или несколько флажков, относящихся к флагам модели, предназначенным для использования.  
  
     Флаги модели отображаются, только если они соответствуют типу данных столбца.  
  
    > [!NOTE]  
    >  После изменения флага модели необходимо повторно обработать модель.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>Получение флагов моделирования, используемых в модели  
  
-   В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте окно DMX-запроса и введите запрос наподобие следующего:  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Флаги моделирования (интеллектуальный анализ данных)](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
