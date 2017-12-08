---
title: "Основные сведения о входных файлах, применяемых для создания скрипта развертывания | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 84106e3dcb54700770d8441d78634767feb5b9da
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="deployment-script-files---input-used-to-create-deployment-script"></a>Файлы скриптов развертывания - входных данных используется для создания скрипта развертывания
  При построении [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает файлы для проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]помещает эти файлы в выходной папке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. По умолчанию в качестве папки проекта используется \Bin. В следующей таблице перечислены XML-файлы, которые создает среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
|Файл|Description|  
|---------------|-----------------|  
|\<*имя проекта*> .asdatabase|XMLA-файл для многомерной или проектов табличной модели 1100 или 1103, или файл JSON для табличных 1200 и выше проекты модели. Содержит декларативные определения всех объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта.|  
|\<*имя проекта*> .deploymenttargets|Содержит имя экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и базы данных, в которой будут созданы объекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|\<*имя проекта*> .configsettings|Содержит параметры, которые относятся к окружению, например сведения о соединении с источником данных и о месте хранения объектов. Параметры в этом файле переопределяют параметры в \< *имя проекта*> asdatabase-файл.|  
|\<*имя проекта*> .deploymentoptions|Содержит параметры развертывания, которые указывают, является ли развертывание транзакционным и нужно ли обрабатывать объекты после развертывания.|  
  
> [!NOTE]  
>  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] пароли никогда не хранятся в файлах проектов.  
  
## <a name="modifying-the-input-files"></a>Изменение входных файлов  
 Изменения значений во входных файлах или значений, полученных из входных файлов, дает возможность изменить назначение развертывания, параметры конфигурации и параметры развертывания, не редактируя весь \< *проекта имя*> файла .asdatabase (или весь скрипт-файл, если скрипт сформирован из существующей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных). Благодаря возможности редактирования отдельных файлов можно легко создавать различные скрипты развертывания для разных целей.  
  
 Следующие разделы содержат сведения об изменении значений в различных входных файлах:  
  
-   [Указание целевого объекта установки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)  
  
-   [Указание параметров развертывания секций и ролей](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [Указание настроек конфигурации для развертывания решения](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
-   [Указание параметров обработки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>См. также:  
 [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Основные сведения о скрипте развертывания служб Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  
