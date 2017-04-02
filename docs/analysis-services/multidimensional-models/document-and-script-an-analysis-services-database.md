---
title: "Документирование и работа со скриптами в базе данных служб Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML для аналитики, скрипты"
  - "XMLA, скрипты"
  - "скрипты [службы Analysis Services], базы данных"
  - "документирование баз данных"
  - "базы данных [службы Analysis Services], документирование"
  - "базы данных [службы Analysis Services], скрипты"
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 35
---
# Документирование и работа со скриптами в базе данных служб Analysis Services
  После того как база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развернута, вы можете использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для вывода метаданных базы данных или объекта, содержащегося в ней, в качестве скрипта XML для аналитики (XMLA). Можно вывести этот скрипт в новое окно **Редактор запросов XML для аналитики** , в файл или в буфер обмена. Дополнительные сведения о языке XMLA см. в разделе [Справочник по языку ASSL (ASSL для XMLA)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Сформированный скрипт XML для аналитики использует элементы языка скриптов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (ASSL) для определения объектов, содержащихся в скрипте. Если создан скрипт CREATE, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Создать** и элементы ASSL, которые могут быть использованы для создания всей структуры базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в экземпляре. Если создан скрипт ALTER, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Изменить** и элементы ASSL, которые могут быть использованы для восстановления структуры существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в состояние, в котором она находилась на момент создания скрипта.  
  
 Созданный скрипт XML для аналитики из базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать различными способами, в том числе:  
  
-   для поддержки скрипта резервного копирования, который позволяет повторно создавать разрешения и объекты базы данных;  
  
-   для создания или обновления кода разработки базы данных;  
  
-   для создания тестовой среды или среды разработки по существующей схеме.  
  
## См. также  
 [Изменение или удаление базы данных служб Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Элемент Alter (XMLA)](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Элемент Create (XMLA)](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  