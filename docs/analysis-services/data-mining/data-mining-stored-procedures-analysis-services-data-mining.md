---
title: "Хранимые процедуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "хранимые процедуры [службы Analysis Services], интеллектуальный анализ данных"
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Хранимые процедуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)
  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают хранимые процедуры, которые можно писать на любом управляемом языке. Поддерживаются управляемые языки программирования [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, C# и управляемый C++. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] хранимые процедуры можно вызывать напрямую с помощью инструкции **CALL** или в запросе DMX.  
  
 Дополнительные сведения о вызове хранимых процедур служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Вызов хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md).  
  
 Общие сведения о возможностях программирования служб [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] см. в разделе [Программирование интеллектуального анализа данных](../../analysis-services/data-mining-programming.md).  
  
 Дополнительные сведения о программировании объектов интеллектуального анализа данных см. в статье «[SQL Server Data Mining Programmability (Возможности программирования интеллектуального анализа данных SQL Server)](http://go.microsoft.com/fwlink/?LinkId=93735)» в библиотеке MSDN.  
  
> [!NOTE]  
>  При запросах к моделям интеллектуального анализа, особенно при тестировании новых решений для интеллектуального анализа данных, удобно вызывать системные хранимые процедуры, которые используются внутренне модулем интеллектуального анализа данных. Можно просматривать имена этих хранимых процедур, используя [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для создания трассировки на сервере служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а затем создавая, просматривая и запрашивая модели интеллектуального анализа данных. Однако [!INCLUDE[msCoName](../../includes/msconame-md.md)] не гарантирует совместимость системных хранимых процедур разных версий, поэтому их ни в коем случае нельзя вызывать в рабочей среде. Вместо этого для обеспечения совместимости следует создавать собственные запросы с помощью расширения интеллектуального анализа данных или XML/A.  
  
## В этом разделе  
  
-   [SystemGetCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## Справочник  
 [Создание скриптов для административных задач в службах Analysis Services](../../analysis-services/instances/script-administrative-tasks-in-analysis-services.md)  
  
## См. также  
 [Перекрестная проверка (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [Вкладка "Перекрестная проверка" (представление диаграммы точности интеллектуального анализа данных)](../Topic/Cross-Validation%20Tab%20\(Mining%20Accuracy%20Chart%20View\).md)   
 [Вызов хранимой процедуры](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  