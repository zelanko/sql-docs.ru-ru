---
title: Document and Script базы данных служб Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7862be07bd3b01db8dcc2a0beb115a883e4550e7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="document-and-script-an-analysis-services-database"></a>Документирование и работа со скриптами в базе данных служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  После того как база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развернута, вы можете использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для вывода метаданных базы данных или объекта, содержащегося в ней, в качестве скрипта XML для аналитики (XMLA). Можно вывести этот скрипт в новое окно **Редактор запросов XML для аналитики** , в файл или в буфер обмена. Дополнительные сведения о языке XMLA см. в разделе [Справочник по языку ASSL (ASSL для XMLA)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Сформированный скрипт XML для аналитики использует элементы языка скриптов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (ASSL) для определения объектов, содержащихся в скрипте. Если создан скрипт CREATE, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Создать** и элементы ASSL, которые могут быть использованы для создания всей структуры базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в экземпляре. Если создан скрипт ALTER, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Изменить** и элементы ASSL, которые могут быть использованы для восстановления структуры существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в состояние, в котором она находилась на момент создания скрипта.  
  
 Созданный скрипт XML для аналитики из базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать различными способами, в том числе:  
  
-   для поддержки скрипта резервного копирования, который позволяет повторно создавать разрешения и объекты базы данных;  
  
-   для создания или обновления кода разработки базы данных;  
  
-   для создания тестовой среды или среды разработки по существующей схеме.  
  
## <a name="see-also"></a>См. также  
 [Изменение или удаление базы данных служб Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Элемент ALTER &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Создать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  
