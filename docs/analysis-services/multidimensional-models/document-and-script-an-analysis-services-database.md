---
title: "Document and Script базы данных служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ceb4145368b88ecc523dc7c5a3b96406bb383c4a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="document-and-script-an-analysis-services-database"></a>Документирование и работа со скриптами в базе данных служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]После [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] база данных развернута, можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для вывода метаданных базы данных или объекта, содержащегося в базе данных, как XML для аналитики (XMLA) скрипта. Можно вывести этот скрипт в новое окно **Редактор запросов XML для аналитики** , в файл или в буфер обмена. Дополнительные сведения о языке XMLA см. в разделе [Справочник по языку ASSL (ASSL для XMLA)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Сформированный скрипт XML для аналитики использует элементы языка скриптов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (ASSL) для определения объектов, содержащихся в скрипте. Если создан скрипт CREATE, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Создать** и элементы ASSL, которые могут быть использованы для создания всей структуры базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в экземпляре. Если создан скрипт ALTER, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Изменить** и элементы ASSL, которые могут быть использованы для восстановления структуры существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в состояние, в котором она находилась на момент создания скрипта.  
  
 Созданный скрипт XML для аналитики из базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать различными способами, в том числе:  
  
-   для поддержки скрипта резервного копирования, который позволяет повторно создавать разрешения и объекты базы данных;  
  
-   для создания или обновления кода разработки базы данных;  
  
-   для создания тестовой среды или среды разработки по существующей схеме.  
  
## <a name="see-also"></a>См. также  
 [Изменение или удаление базы данных служб Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Изменить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Создать элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  
