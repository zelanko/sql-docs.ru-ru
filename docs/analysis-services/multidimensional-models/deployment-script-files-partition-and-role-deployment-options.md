---
title: "Указание параметров развертывания ролей и секций | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6595d80eeba45415ac501182c31025478899711
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deployment-script-files---partition-and-role-deployment-options"></a>Файлы скриптов развертывания - параметры секций и ролей развертывания
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает параметры развертывания секций и ролей из \< *имя проекта*> .deploymentoptions файла. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует параметры развертывания секций и ролей текущего проекта при \< *имя проекта*> .deploymentoptions файл создается. Дополнительные сведения о настройках конфигурации см. в разделе [Understanding the Input Files Used to Create the Deployment Script](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Просмотр параметров развертывания секций и ролей  
 Параметры развертывания в \< *имя проекта*> .deploymentoptions включают следующее:  
  
 **Параметры развертывания секций**  
 \< *Имя проекта*> .deploymentoptions указывает, будут ли существующие секции в целевой базе данных сохраняться или перезаписываться (по умолчанию). Если существующие секции сохраняются, то будут развернуты только новые секции, а секции и статистические схемы во всех существующих группах мер останутся неизменными.  
  
> [!NOTE]  
>  Если группа мер, на которой основана секция, удаляется, то секция также автоматически удаляется.  
  
 **Параметры развертывания ролей**  
 \< *Имя проекта*> .deploymentoptions указывает один из следующих параметров развертывания ролей:  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и развертываются только новые роли и члены ролей.  
  
-   Все существующие роли и члены ролей в целевой базе данных заменяются развертываемыми ролями и членами.  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и новые роли не развертываются.  
  
-   **Примечание** При сохранении существующих ролей или членов ролей связанные с ними разрешения теряются. Разрешения содержатся в защищаемых объектах, а не в ролях безопасности, с которыми они связаны. Дополнительные сведения о работе с этим поведением с помощью мастера развертывания служб Analysis Service см. в разделе «Сохранение ролей и членов ролей» в базе знаний Майкрософт.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Изменение параметров развертывания секций и ролей  
 Может возникнуть необходимость развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта с помощью разных параметров секций и ролей, отличающиеся от хранящихся в \< *имя проекта*> .deploymentoptions файла. Например, может понадобиться сохранить существующие секции, роли и члены ролей вместо замены всех существующих секций, ролей и членов, как указано в \< *имя проекта*> .deploymentoptions файла.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, невозможно изменить настройки секций и ролей в самом проекте, так как  *\<имя проекта >* **страницы свойств**  диалоговое окно в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] эти параметры не отображаются. Для изменения параметров развертывания для ролей и секций необходимо изменить эти данные в \< *имя проекта*> .deploymentoptions файл. Ниже приведена процедура изменения параметров развертывания секций и ролей в \< *имя проекта*> .deploymentoptions файла.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Изменение развертывания секций и ролей после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры развертывания секций и ролей** укажите новые параметры развертывания для секций и ролей.  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. (Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).)  
  
     —или—  
  
-   Откройте \< *имя проекта*> .deploymentoptions в любом текстовом редакторе и вручную изменить параметры.  
  
## <a name="see-also"></a>См. также:  
 [Указание целевого объекта установки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Задание параметров конфигурации для развертывания решения](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Указание параметров обработки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  

