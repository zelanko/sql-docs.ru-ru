---
title: "Обработать структуру интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
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
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2e9c6f31a8701571b2d9be03eecd34050757e7a7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="process-a-mining-structure"></a>обработать структуру интеллектуального анализа данных
  Перед тем как получить возможность просмотра или работы с моделями интеллектуального анализа данных, связанными со структурой интеллектуального анализа данных, необходимо развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и обработать структуру интеллектуального анализа данных, а также модель интеллектуального анализа данных. Также при внесении изменений в структуру интеллектуального анализа данных или модель интеллектуального анализа данных будет выдано приглашение к их повторному развертыванию и обработке. При обработке структуры на вкладке **Структура интеллектуального анализа данных** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] обрабатываются все связанные с ней модели.  
  
 Обработка структуры интеллектуального анализа данных производится с помощью следующих средств.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA: команда Process  
  
 Дополнительные сведения об обработке отдельных моделей см. в разделе [Обработка модели интеллектуального анализа данных](../../analysis-services/data-mining/process-a-mining-model.md).  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>Обработка структуры интеллектуального анализа данных и всех связанных с ней моделей интеллектуального анализа данных с помощью SQL Server Data Tools  
  
1.  Выберите пункт **Обработать структуру интеллектуального анализа данных и все модели** из пункта меню **Модель интеллектуального анализа данных** в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
     При внесении изменений в структуру будет выдано приглашение к повторному развертыванию структуры перед обработкой моделей. Нажмите кнопку **Да**.  
  
2.  Нажмите кнопку **запуска** в **Обработка структуры интеллектуального анализа данных — \<структуры >** диалоговое окно.  
  
     Откроется диалоговое окно **Ход обработки** , отображающее подробные сведения об обработке модели.  
  
3.  Нажмите кнопку **Закрыть** в диалоговом окне **Ход обработки** после завершения обработки моделей.  
  
4.  Нажмите кнопку **закрыть** в **Обработка структуры интеллектуального анализа данных — \<структуры >** диалоговое окно.  
  
## <a name="see-also"></a>См. также:  
 [Задачи и инструкции по структуре интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

