---
title: "Развертывание решений модели с использованием мастера развертывания | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "мастер развертывания служб Analysis Services"
  - "развертывание [службы Analysis Services], мастер развертывания служб Analysis Services"
  - "развертывания служб Analysis Services], мастер развертывания служб Analysis Services"
  - "мастер развертывания служб Analysis Services, о мастере развертывания служб Analysis Services"
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
caps.latest.revision: 39
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Развертывание решений модели с использованием мастера развертывания
  Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует выходные XML-файлы, создаваемые в проекте служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в качестве входных. Эти входные файлы можно легко изменить для настройки развертывания проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Сформированный скрипт развертывания можно затем либо сразу запустить, либо сохранить и запустить позднее.  
  
 Развертывание можно выполнить при помощи мастера. Также можно автоматизировать развертывание или использовать функцию синхронизации. При больших размерах развернутой базы данных на целевых системах рекомендуется использовать секции. Создание и заполнение секций также можно автоматизировать с помощью объектов \(AMO\).  
  
> [!IMPORTANT]  
>  Ни выходные XML-файлы, ни скрипт развертывания не будут содержать идентификаторов пользователя или паролей, если они вводились в строке соединения для источника данных или для олицетворения. Поскольку в данном сценарии они необходимы для обработки, добавьте их вручную. Если в ходе развертывания не выполнится обработка, то эти сведения для соединения и олицетворения при необходимости можно добавить после развертывания. Если в ходе развертывания выполнится обработка, то можно добавить эти сведения с помощью мастера или добавить их в скрипт развертывания после его сохранения.  
  
## В этом разделе  
 В следующих подразделах рассматривается работа с мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входными файлами и скриптом развертывания:  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|Содержит описание различных способов запуска мастера развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md)|Содержит описание файлов, используемых мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в качестве входных значений, содержимого каждого из таких файлов, а также содержит ссылки на подразделы, в которых описывается, как изменять значения в каждом из входных файлов.|  
|[Основные сведения о скрипте развертывания служб Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|Содержит описание скрипта развертывания и его выполнения.|  
  
## См. также:  
 [Развертывание решений модели с помощью XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Синхронизация баз данных служб Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md)   
 [Развертывание решений моделей с использованием программы развертывания](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  