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
manager: craigg
ms.openlocfilehash: b9b36013f13360a2afcf9546cd1e286b35ae4acd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075356"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Указание параметров развертывания секций и ролей
  Мастер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывания считывает параметры развертывания секций и ролей из \<файла с *именем проекта*>. deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при сборке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует параметры развертывания секций и ролей текущего проекта при \<создании *имени проекта*>. deploymentoptions. Дополнительные сведения о настройках конфигурации см. в разделе [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Просмотр параметров развертывания секций и ролей  
 Параметры развертывания в файле с \< *именем проекта*>. deploymentoptions включают следующее:  
  
 **Параметры развертывания секций**  
 \< *Имя проекта*>. deploymentoptions указывает, будут ли сохранены или перезаписаны существующие секции в целевой базе данных (по умолчанию). Если существующие секции сохраняются, то будут развернуты только новые секции, а секции и статистические схемы во всех существующих группах мер останутся неизменными.  
  
> [!NOTE]  
>  Если группа мер, на которой основана секция, удаляется, то секция также автоматически удаляется.  
  
 **Параметры развертывания ролей**  
 \< *Имя проекта*>. deploymentoptions указывает один из следующих вариантов развертывания роли:  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и развертываются только новые роли и члены ролей.  
  
-   Все существующие роли и члены ролей в целевой базе данных заменяются развертываемыми ролями и членами.  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и новые роли не развертываются.  
  
-   **Примечание** При сохранении существующих ролей или членов ролей связанные с ними разрешения теряются. Разрешения содержатся в защищаемых объектах, а не в ролях безопасности, с которыми они связаны. Дополнительные сведения о работе с этим поведением с помощью мастера развертывания служб Analysis Services см. в разделе "сохраните роли и члены" в базе знаний Майкрософт.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Изменение параметров развертывания секций и ролей  
 Может потребоваться развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект, используя параметры раздела и роли, отличные от тех, которые хранятся в \<файле *Project Name*>. deploymentoptions. Например, может потребоваться хранить существующие секции, роли и члены ролей вместо того, чтобы заменять все существующие секции, роли и члены, как указано в \<файле *Project*>. deploymentoptions.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекте, нельзя изменить параметры секций и ролей в проекте, так как в диалоговом окне **страницы свойств** " * \<имя проекта>* " [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в не отображаются эти параметры. Если вы хотите изменить параметры развертывания для ролей и секций, необходимо изменить эти сведения в \<файле *Project Name*>. deploymentoptions. В следующей процедуре описывается изменение параметров развертывания секций и ролей в \< *имени проекта*>. deploymentoptions.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Изменение развертывания секций и ролей после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры развертывания секций и ролей** укажите новые параметры развертывания для секций и ролей.  
  
     -или-  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. (Дополнительные сведения о режиме файла ответов см. [в разделе Запуск мастера развертывания Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     -или-  
  
-   \<Откройте *имя проекта*>. deploymentoptions в любом текстовом редакторе и вручную измените параметры.  
  
## <a name="see-also"></a>См. также  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)   
 [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
  
