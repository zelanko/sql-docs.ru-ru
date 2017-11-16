---
title: "Исключить столбец из модели интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a12584791ec8ea21a1338c09dbc0e5f7ef8f7a62
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="exclude-a-column-from-a-mining-model"></a>исключить столбец из модели интеллектуального анализа данных
  При создании новой модели интеллектуального анализа данных может отсутствовать необходимость использовать все столбцы, существующие в структуре интеллектуального анализа данных, на которой основывается модель. Например, если вы добавили столбец имен заказчиков для детализации, который не требуется использовать при моделировании. Или же может потребоваться создать несколько копий столбца с различной дискретизацией так, чтобы только одна из таких копий использовалась в каждой модели, а остальные пропускались. Также можно избирательно добавлять входные столбцы в некоторые модели для того, чтобы увидеть, как добавленные переменные повлияют на выходной столбец.  
  
 Не требуется создавать новую структуру интеллектуального анализа данных для каждой комбинации столбцов. Вместо этого можно просто отметить столбцы, которые не будут использоваться в конкретной модели.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Исключение столбца из модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите ячейку, которая соответствует столбцу, который необходимо исключить, под соответствующей моделью интеллектуального анализа данных.  
  
2.  Выберите пункт **Пропустить** из раскрывающегося списка.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  

