---
title: "Удалить столбцы из структуры интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5592cefdc8e4e77ec5b6e92ee0d4d671b5df3408
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="remove-columns-from-a-mining-structure"></a>удалить столбцы из структуры интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Конструктор интеллектуального анализа данных можно использовать для удаления столбцов из структуры интеллектуального анализа данных после структура уже был создан. Возможны следующие причины удаления столбца структуры интеллектуального анализа данных.  
  
-   Структура интеллектуального анализа данных содержит несколько копий столбца, и вы хотите избежать дублирования данных в модели.  
  
-   Данные должны быть защищены, но детализация была разрешена.  
  
-   Данные не используются в моделировании и не должны обрабатываться.  
  
 При удалении столбца из структуры интеллектуального анализа данных не производится его удаления из представления источников данных или внешних данных. Удаляются только метаданные. Однако при изменении столбцов, используемых в структуре интеллектуального анализа данных, необходимо выполнить повторную обработку структуры и любых, основанных на ней моделей.  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>Удаление столбца из структуры интеллектуального анализа данных  
  
1.  Перейдите на вкладку **Структура интеллектуального анализа данных** в конструкторе интеллектуального анализа данных.  
  
2.  Разверните дерево для структуры интеллектуального анализа данных для отображения всех столбцов.  
  
3.  Щелкните правой кнопкой мыши столбец, который необходимо удалить, а затем выберите пункт **Удалить**.  
  
4.  В диалоговом окне **Удаление объектов** нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по структуре интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
