---
title: "Указание параметров развертывания секций и ролей | Microsoft Docs"
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
  - "Секции [службы Analysis Services], параметры развертывания"
  - "Развертывания служб Analysis Services, роли"
  - "Развертывания служб Analysis Services, секции"
  - "Мастер развертывания служб Analysis Services, роли"
  - "Мастер развертывания служб Analysis Services, секции"
  - "Развертывание [службы Analysis Services], роли"
  - "Роли [службы Analysis Services], параметры развертывания"
  - "Развертывание [службы Analysis Services], секции"
  - "изменение развертывания ролей"
  - "изменение развертывания секций"
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Указание параметров развертывания секций и ролей
  Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] считывает параметры развертывания секций и ролей из файла \<*имя_проекта*>.deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует параметры развертывания секций и ролей текущего проекта при создании файла \<*имя_проекта*>.deploymentoptions. Дополнительные сведения о настройках конфигурации см. в разделе [Understanding the Input Files Used to Create the Deployment Script](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md).  
  
## Просмотр параметров развертывания секций и ролей  
 Параметры развертывания в файле \<*имя_проекта*>.deploymentoptions включают следующее:  
  
 **Параметры развертывания секций**  
 Файл \<*имя_проекта*>.deploymentoptions указывает, будут ли существующие секции в целевой базе данных сохраняться или перезаписываться (по умолчанию). Если существующие секции сохраняются, то будут развернуты только новые секции, а секции и статистические схемы во всех существующих группах мер останутся неизменными.  
  
> [!NOTE]  
>  Если группа мер, на которой основана секция, удаляется, то секция также автоматически удаляется.  
  
 **Параметры развертывания ролей**  
 Файл \<*имя_проекта*>.deploymentoptions указывает один из следующих параметров развертывания ролей:  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и развертываются только новые роли и члены ролей.  
  
-   Все существующие роли и члены ролей в целевой базе данных заменяются развертываемыми ролями и членами.  
  
-   Существующие роли и члены ролей в целевой базе данных сохраняются, и новые роли не развертываются.  
  
-   **Примечание** При сохранении существующих ролей или членов ролей связанные с ними разрешения теряются. Разрешения содержатся в защищаемых объектах, а не в ролях безопасности, с которыми они связаны. Дополнительные сведения о работе с этим поведением с помощью мастера развертывания служб Analysis Service см. в разделе «Сохранение ролей и членов ролей» в базе знаний Майкрософт.  
  
## Изменение параметров развертывания секций и ролей  
 Может возникнуть необходимость развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью параметров секций и ролей, отличающихся от хранящихся в файле \<*имя_проекта*>.deploymentoptions. Например, может понадобиться сохранить существующие секции, роли и участников ролей вместо замены всех существующих секций, ролей и участников, как указано в файле \<*имя_проекта*>.deploymentoptions.  
  
 Чтобы изменить развертывание секций и ролей в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], нельзя изменять настройки секций и ролей в самом проекте, так как в диалоговом окне *\<имя_проекта>* **Страницы свойств** в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] эти параметры не отображаются. Если нужно изменить параметры развертывания для ролей и секций, необходимо изменить эти данные в самом файле \<*имя_проекта*>.deploymentoptions. В следующей процедуре описано изменение параметров развертывания секций и ролей в файле \<*имя_проекта*>.deploymentoptions.  
  
#### Изменение развертывания секций и ролей после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры развертывания секций и ролей** укажите новые параметры развертывания для секций и ролей.  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. (Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).)  
  
     —или—  
  
-   Откройте файл \<*имя_проекта*>.deploymentoptions в любом текстовом редакторе и измените параметры вручную.  
  
## См. также  
 [Указание целевого объекта установки](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [Указание настроек конфигурации для развертывания решения](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [Указание параметров обработки](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  