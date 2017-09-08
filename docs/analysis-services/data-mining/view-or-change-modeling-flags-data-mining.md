---
title: "Просмотр или изменение флагов модели (интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cbffc4a5312dc83976915653141247d27dc8eae4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="view-or-change-modeling-flags-data-mining"></a>Просмотр или изменение флагов модели (интеллектуальный анализ данных)
  Флаги модели представляют собой свойства, которые можно задать в столбце структуры интеллектуального анализа данных или столбцах модели интеллектуального анализа данных для определения того, как алгоритм обрабатывает данные во время анализа.  
  
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
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Флаги моделирования (интеллектуальный анализ данных)](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
