---
title: Основные сведения о входных файлах, применяемых для создания скрипта развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a03735b1d412a7501ab59f88288c32ef7ec5514c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726338"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a>Основные сведения о входных файлах, применяемых для создания скрипта развертывания
  При сборке проекта [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] формирует XML-файлы. Среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] помещает эти XML-файлы в выходную папку проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. По умолчанию в качестве папки проекта используется \Bin. В следующей таблице перечислены XML-файлы, которые создает среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
|XMLA-файл|Описание|  
|---------------|-----------------|  
|\<*имя проекта*> .asdatabase|Содержит декларативные определения всех объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта.|  
|\<*имя проекта*> .deploymenttargets|Содержит имя экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и базы данных, в которой будут созданы объекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|\<*имя проекта*> .configsettings|Содержит параметры, которые относятся к окружению, например сведения о соединении с источником данных и о месте хранения объектов. Параметры в этом файле переопределяют параметры в \< *имя_проекта*> файл с расширением asdatabase.|  
|\<*имя проекта*> .deploymentoptions|Содержит параметры развертывания, которые указывают, является ли развертывание транзакционным и нужно ли обрабатывать объекты после развертывания.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] не хранит пароли в файлах проектов.  
  
## <a name="modifying-the-input-files"></a>Изменение входных файлов  
 Путем изменения значений во входных файлах или значения, полученные из входных файлов, можно изменить назначение развертывания, а также параметры конфигурации и параметры развертывания, не редактируя весь \< *проекта имя*> файла .asdatabase (или весь XMLA-файл скрипта, если скрипт сформирован из существующей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных). Благодаря возможности редактирования отдельных файлов можно легко создавать различные скрипты развертывания для разных целей.  
  
 Следующие разделы содержат сведения об изменении значений в различных входных файлах:  
  
-   [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)  
  
-   [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [Указание настроек конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>См. также  
 [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Основные сведения о скрипте развертывания служб Analysis Services](understanding-the-analysis-services-deployment-script.md)  
  
  
