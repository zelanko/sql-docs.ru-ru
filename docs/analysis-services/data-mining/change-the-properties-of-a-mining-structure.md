---
title: "Изменить свойства структуры интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 908bf89105dbcfc4c61a4018c92a8cee71237fb9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="change-the-properties-of-a-mining-structure"></a>изменить свойства структуры интеллектуального анализа данных
  Имеется два вида свойств структур интеллектуального анализа данных (свойства обоих видов могут изменяться):  
  
-   Свойства структуры интеллектуального анализа данных, влияющие на структуру в целом  
  
-   Свойства отдельных столбцов в структуре  
  
 Учтите, что некоторые свойства зависят от значений других свойств. Например, нельзя задать свойства, управляющие сегментированием (например, <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> или <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>), пока тип данных столбца не будет установлен в значение **Discretized**.  
  
 Дополнительные сведения о свойствах структур интеллектуального анализа данных см. в разделе [Столбцы структуры интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>Изменение свойств структуры интеллектуального анализа данных  
  
1.  На вкладке **Структура интеллектуального анализа данных** конструктора интеллектуального анализа данных щелкните правой кнопкой мыши структуру интеллектуального анализа данных или столбец в такой структуре, а затем выберите пункт **Свойства**.  
  
     В правой части экрана появится окно **Свойства** , если оно еще не было открыто.  
  
2.  В окне **Свойства** выберите значение, соответствующее свойству, которое нужно изменить, и введите новое значение.  
  
     Новое значение вступает в силу после выбора другого элемента в конструкторе.  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи и инструкции по структуре интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

