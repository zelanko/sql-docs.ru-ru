---
title: "Основные сведения о входных файлах, применяемых для создания скрипта развертывания | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
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
  - "входные файлы [службы Analysis Services]"
  - "Мастер развертывания служб Analysis Services, скрипты"
  - "развертывание [службы Analysis Services], входные файлы"
  - "мастер развертывания служб Analysis Services, входные файлы"
  - "скрипты [службы Analysis Services], развертывание"
  - "развертывания служб Analysis Services, входные файлы"
  - "изменение входных файлов"
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Основные сведения о входных файлах, применяемых для создания скрипта развертывания
  При сборке проекта [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] формирует XML-файлы. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] помещает эти XML-файлы в выходную папку проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. По умолчанию в качестве папки проекта используется \\Bin. В следующей таблице перечислены XML-файлы, которые создает среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
|XMLA-файл|Description|  
|---------------|-----------------|  
|\<*имя_проекта*\>.asdatabase|Содержит декларативные определения всех объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта.|  
|\<*имя_проекта*\>.deploymenttargets|Содержит имя экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и базы данных, в которой будут созданы объекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|\<*имя_проекта*\>.configsettings|Содержит параметры, которые относятся к окружению, например сведения о соединении с источником данных и о месте хранения объектов. Параметры в этом файле переопределяют параметры в файле \<*имя_проекта*\>.asdatabase.|  
|\<*имя проекта*\>.deploymentoptions|Содержит параметры развертывания, которые указывают, является ли развертывание транзакционным и нужно ли обрабатывать объекты после развертывания.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] не хранит пароли в файлах проектов.  
  
## Изменение входных файлов  
 Вы можете изменить целевое расположение развертывания, а также параметры конфигурации и развертывания без необходимости редактировать весь файл\<*имя_проекта*\>.asdatabase \(или весь XMLA-файл скрипта, если скрипт создается из существующей базы данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]\). Для этого измените значения во входных файлах или значения, полученные из входных файлов. Благодаря возможности редактирования отдельных файлов можно легко создавать различные скрипты развертывания для разных целей.  
  
 Следующие разделы содержат сведения об изменении значений в различных входных файлах:  
  
-   [Указание целевого объекта установки](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)  
  
-   [Указание параметров развертывания секций и ролей](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)  
  
-   [Указание настроек конфигурации для развертывания решения](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
-   [Указание параметров обработки](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
## См. также:  
 [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Основные сведения о скрипте развертывания служб Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  