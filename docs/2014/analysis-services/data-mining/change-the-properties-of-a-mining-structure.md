---
title: Изменение свойств структуры интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4b56fc1d00fe639d78d5f01fe44554b7fe2d7cc7
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84524960"
---
# <a name="change-the-properties-of-a-mining-structure"></a>изменить свойства структуры интеллектуального анализа данных
  Имеется два вида свойств структур интеллектуального анализа данных (свойства обоих видов могут изменяться):  
  
-   Свойства структуры интеллектуального анализа данных, влияющие на структуру в целом  
  
-   Свойства отдельных столбцов в структуре  
  
 Учтите, что некоторые свойства зависят от значений других свойств. Например, нельзя задать свойства, управляющие сегментированием (например, <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> или <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>), пока тип данных столбца не будет установлен в значение `Discretized`.  
  
 Дополнительные сведения о свойствах структур интеллектуального анализа данных см. в разделе [Столбцы структуры интеллектуального анализа данных](mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>Изменение свойств структуры интеллектуального анализа данных  
  
1.  На вкладке **Структура интеллектуального анализа данных** конструктора интеллектуального анализа данных щелкните правой кнопкой мыши структуру интеллектуального анализа данных или столбец в такой структуре, а затем выберите пункт **Свойства**.  
  
     В правой части экрана появится окно **Свойства** , если оно еще не было открыто.  
  
2.  В окне **Свойства** выберите значение, соответствующее свойству, которое нужно изменить, и введите новое значение.  
  
     Новое значение вступает в силу после выбора другого элемента в конструкторе.  
  
## <a name="see-also"></a>См. также:  
 [Задачи и инструкции по структуре интеллектуального анализа данных](mining-structure-tasks-and-how-tos.md)  
  
  
