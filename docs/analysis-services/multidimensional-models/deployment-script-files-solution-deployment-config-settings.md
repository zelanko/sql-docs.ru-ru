---
title: "Задание параметров конфигурации для развертывания решения | Документы Microsoft"
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
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 24861b3e40c12d28c0bdbf25772fabad9f6c1107
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deployment-script-files---solution-deployment-config-settings"></a>Файлы скриптов развертывания - параметры конфигурации для развертывания решения
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает секций и ролей варианты развертывания, которые можно использовать в скрипте развертывания, из \< *имя проекта*> .configsettings файла. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует настройки конфигурации текущего проекта для создания \< *имя проекта*> .configsettings файла.  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>Просмотр настроек конфигурации для развертывания  
 Ниже приведены настройки конфигурации, хранящиеся в \< *имя проекта*> .configsettings файла:  
  
-   **Data Source Connection Strings** . Это строки подключений для каждого источника данных, основанные на значениях, заданных в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Идентификатор пользователя и пароль всегда удаляются из строки соединения до того, как оставшаяся часть строки сохраняется в этом файле. Однако если мастер развертывания выполняет развертывание непосредственно в экземпляре служб Analysis Services, можно ввести нужный идентификатор пользователя и пароль в мастере, что обеспечит успешную обработку развертываемой базы данных. Эти сведения о соединении не сохраняются в самом скрипте развертывания, если он сохраняется мастером развертывания.  
  
-   **Impersonation Accounts** . Этот параметр задает имя пользователя, которое службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют для запуска инструкций в каждом источнике данных. Если учетная запись олицетворения не задана, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют собственную учетную запись входа для запуска инструкций. Если учетной записи входа служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставлены разрешения непосредственно в источнике данных, то все администраторы баз данных во всех базах данных в экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют доступ к источнику данных посредством этой учетной записи входа. Если учетная запись пользователя и пароль указаны, то эти сведения всегда удаляются до того, как данные для олицетворения сохраняются в этом файле. Однако если мастер развертывания выполняет развертывание непосредственно в экземпляре служб Analysis Services, можно ввести нужный идентификатор пользователя и пароль в мастере, что обеспечит успешную обработку развертываемой базы данных. Эти сведения об олицетворении не сохранятся в самом скрипте развертывания, если он сохраняется мастером развертывания.  
  
-   **Key Error Log Files** . Этот параметр задает имя и путь файла журнала ошибок ключа для каждого куба, группы мер, секции и измерения в базе данных.  
  
-   **Storage Locations** . Этот параметр задает место хранения для каждого куба, группы мер и секции в базе данных. Если для объекта не введено значение, то мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует местоположение по умолчанию для объекта. Например, секции используют местоположение для группы мер, группы мер используют местоположение для куба, а кубы используют местоположение по умолчанию для объектов в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Место хранения может быть локальным путем или путем в формате UNC.  
  
-   **Report Server** . Этот параметр задает сервер отчетов и местоположение папки для каждого действия отчета, определенного в каждом кубе в базе данных.  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>Изменение настроек конфигурации для развертывания  
 В некоторых случаях может потребоваться развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, используя другие настройки конфигурации вместо тех, которые хранятся в \< *имя проекта*> .configsettings файла. Например, может быть необходимо изменить строку соединения с одним или несколькими источниками данных или задать места хранения для конкретных секций или групп мер.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, необходимо изменить эти данные в \< *имя проекта*> .configsettings файла, как описано в следующей процедуре. Невозможно изменить настройки секций и ролей в самом проекте, так как  *\<имя проекта >* **страницы свойств** диалоговое окно в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] эти параметры не отображаются.  
  
> [!NOTE]  
>  Настройки конфигурации могут применяться ко всем объектам или только ко вновь созданным объектам. Применяйте параметры конфигурации ко вновь созданным объектам только при развертывании дополнительных объектов в ранее развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , если не нужно перезаписывать существующие объекты. Чтобы указать ли параметры конфигурации применяются ко всем объектам или только ко вновь созданным объектам, установите этот параметр \< *имя проекта*> .deploymentoptions файла. Дополнительные сведения см. в статье [Указание параметров развертывания секций и ролей](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md).  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>Изменение настройки конфигурации после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры конфигурации** укажите параметры конфигурации для развертываемых объектов.  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —или—  
  
-   Изменить \< *имя проекта*> .configsettings файл, используя любой текстовый редактор.  
  
## <a name="see-also"></a>См. также:  
 [Указание целевого объекта установки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров развертывания секций и ролей](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [Указание параметров обработки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  

