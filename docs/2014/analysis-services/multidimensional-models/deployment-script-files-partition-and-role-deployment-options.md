---
title: Указание секций и параметров развертывания ролей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: 14a547098cf72ac4b4f1c49044aba1bb2f024adc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055536"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Указание параметров развертывания секций и ролей
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает параметры развертывания секций и ролей из \< *имя_проекта*> .deploymentoptions файл. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует параметры развертывания секций и ролей текущего проекта при \< *имя_проекта*> .deploymentoptions файл создается. Дополнительные сведения о настройках конфигурации см. в разделе [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Просмотр параметров развертывания секций и ролей  
 Параметры развертывания в \< *имя_проекта*> .deploymentoptions включают следующее:  
  
 **Параметры развертывания секций**  
 \< *Имя_проекта*> .deploymentoptions указывает ли существующие секции в целевой базе данных сохраняться или перезаписываться (по умолчанию). Если существующие секции сохраняются, то будут развернуты только новые секции, а секции и статистические схемы во всех существующих группах мер останутся неизменными.  
  
> [!NOTE]  
>  Если группа мер, на которой основана секция, удаляется, то секция также автоматически удаляется.  
  
 **Параметры развертывания ролей**  
 \< *Имя_проекта*> .deploymentoptions указывает один из следующих параметров развертывания ролей:  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и развертываются только новые роли и члены ролей.  
  
-   Все существующие роли и члены ролей в целевой базе данных заменяются развертываемыми ролями и членами.  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и новые роли не развертываются.  
  
-   **Примечание** При сохранении существующих ролей или членов ролей связанные с ними разрешения теряются. Разрешения содержатся в защищаемых объектах, а не в ролях безопасности, с которыми они связаны. Дополнительные сведения о работе с этим поведением с помощью мастера развертывания служб Analysis Service см. в разделе «Сохранение ролей и членов ролей» в базе знаний Майкрософт.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Изменение параметров развертывания секций и ролей  
 Может возникнуть необходимость развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта с помощью разных параметров секций и ролей, отличающихся от хранящихся в \< *имя_проекта*> .deploymentoptions файл. Например, может понадобиться сохранить существующие секции, роли и члены ролей вместо замены всех существующих секций, ролей и членов, как указано в \< *имя_проекта*> .deploymentoptions файл.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, невозможно изменить настройки секций и ролей в проекте, так как  *\<имя проекта >* **страницы свойств**  диалогового окна в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] эти параметры не отображаются. Если вы хотите изменить параметры развертывания для ролей и секций, необходимо изменить эти данные в \< *имя_проекта*> сам файл .deploymentoptions. Следующая процедура описывает изменение параметров развертывания секций и ролей в \< *имя_проекта*> .deploymentoptions файл.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Изменение развертывания секций и ролей после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры развертывания секций и ролей** укажите новые параметры развертывания для секций и ролей.  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. (Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     —или—  
  
-   Откройте \< *имя_проекта*> .deploymentoptions в любом текстовом редакторе и вручную изменить параметры.  
  
## <a name="see-also"></a>См. также  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание настроек конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)   
 [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
  
