---
title: Указание параметров развертывания секций и ролей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4f2f5bb2f3f39636541d5aea5b931b1dcc72534
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546866"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Указание параметров развертывания секций и ролей
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Мастер развертывания считывает параметры развертывания секций и ролей из \<*project name*> файла deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при сборке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует параметры развертывания секций и ролей текущего проекта при \<*project name*> создании файла. deploymentoptions. Дополнительные сведения о настройках конфигурации см. в разделе [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Просмотр параметров развертывания секций и ролей  
 Параметры развертывания в \<*project name*> файле. deploymentoptions включают следующее:  
  
 **Параметры развертывания секций**  
 \<*project name*>Файл. deploymentoptions указывает, сохраняются ли существующие секции в целевой базе данных (по умолчанию). Если существующие секции сохраняются, то будут развернуты только новые секции, а секции и статистические схемы во всех существующих группах мер останутся неизменными.  
  
> [!NOTE]  
>  Если группа мер, на которой основана секция, удаляется, то секция также автоматически удаляется.  
  
 **Параметры развертывания ролей**  
 \<*project name*>Файл. deploymentoptions указывает один из следующих вариантов развертывания роли:  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и развертываются только новые роли и члены ролей.  
  
-   Все существующие роли и члены ролей в целевой базе данных заменяются развертываемыми ролями и членами.  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и новые роли не развертываются.  
  
-   **Примечание** При сохранении существующих ролей или членов ролей связанные с ними разрешения теряются. Разрешения содержатся в защищаемых объектах, а не в ролях безопасности, с которыми они связаны. Дополнительные сведения о работе с этим поведением с помощью мастера развертывания служб Analysis Services см. в разделе "сохраните роли и члены" в базе знаний Майкрософт.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Изменение параметров развертывания секций и ролей  
 Может потребоваться развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект, используя параметры раздела и роли, отличные от тех, которые хранятся в \<*project name*> файле deploymentoptions. Например, можно хранить существующие секции, роли и члены ролей вместо того, чтобы заменять все существующие секции, роли и члены, как указано в \<*project name*> файле deploymentoptions.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекте, нельзя изменить параметры секций и ролей в проекте, так как *\<project name>* диалоговое окно **страницы свойств** в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] не отображает эти параметры. Если вы хотите изменить параметры развертывания для ролей и секций, необходимо изменить эти сведения в \<*project name*> самом файле. deploymentoptions. В следующей процедуре описывается изменение параметров развертывания секций и ролей в \<*project name*> deploymentoptions файле.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Изменение развертывания секций и ролей после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры развертывания секций и ролей** укажите новые параметры развертывания для секций и ролей.  
  
     -или-  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. (Дополнительные сведения о режиме файла ответов см. [в разделе Запуск мастера развертывания Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     -или-  
  
-   Откройте \<*project name*> . deploymentoptions в любом текстовом редакторе и вручную измените параметры.  
  
## <a name="see-also"></a>См. также:  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)   
 [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
  
