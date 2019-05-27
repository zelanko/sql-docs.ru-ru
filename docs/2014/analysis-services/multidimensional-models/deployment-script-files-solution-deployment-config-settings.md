---
title: Указание настроек конфигурации для развертывания решения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8addba32560e136f68e538240f4fce01f826355e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66075268"
---
# <a name="specifying-configuration-settings-for-solution-deployment"></a>Указание настроек конфигурации для развертывания решения
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает секций и ролей варианты развертывания, используемые в скрипте развертывания, из \< *имя_проекта*> .configsettings файл. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует настройки конфигурации текущего проекта для создания \< *имя_проекта*> .configsettings файл.  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>Просмотр настроек конфигурации для развертывания  
 Ниже приведены настройки конфигурации, хранящиеся в \< *имя_проекта*> .configsettings файла:  
  
-   **Data Source Connection Strings** . Это строки подключений для каждого источника данных, основанные на значениях, заданных в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Идентификатор пользователя и пароль всегда удаляются из строки соединения до того, как оставшаяся часть строки сохраняется в этом файле. Однако если мастер развертывания выполняет развертывание непосредственно в экземпляре служб Analysis Services, можно ввести нужный идентификатор пользователя и пароль в мастере, что обеспечит успешную обработку развертываемой базы данных. Эти сведения о соединении не сохраняются в самом скрипте развертывания, если он сохраняется мастером развертывания.  
  
-   **Impersonation Accounts** . Этот параметр задает имя пользователя, которое службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют для запуска инструкций в каждом источнике данных. Если учетная запись олицетворения не задана, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют собственную учетную запись входа для запуска инструкций. Если учетной записи входа служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставлены разрешения непосредственно в источнике данных, то все администраторы баз данных во всех базах данных в экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют доступ к источнику данных посредством этой учетной записи входа. Если учетная запись пользователя и пароль указаны, то эти сведения всегда удаляются до того, как данные для олицетворения сохраняются в этом файле. Однако если мастер развертывания выполняет развертывание непосредственно в экземпляре служб Analysis Services, можно ввести нужный идентификатор пользователя и пароль в мастере, что обеспечит успешную обработку развертываемой базы данных. Эти сведения об олицетворении не сохранятся в самом скрипте развертывания, если он сохраняется мастером развертывания.  
  
-   **Key Error Log Files** . Этот параметр задает имя и путь файла журнала ошибок ключа для каждого куба, группы мер, секции и измерения в базе данных.  
  
-   **Storage Locations** . Этот параметр задает место хранения для каждого куба, группы мер и секции в базе данных. Если для объекта не введено значение, то мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует местоположение по умолчанию для объекта. Например, секции используют местоположение для группы мер, группы мер используют местоположение для куба, а кубы используют местоположение по умолчанию для объектов в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Место хранения может быть локальным путем или путем в формате UNC.  
  
-   **Report Server** . Этот параметр задает сервер отчетов и местоположение папки для каждого действия отчета, определенного в каждом кубе в базе данных.  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>Изменение настроек конфигурации для развертывания  
 В некоторых случаях может потребоваться развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект, используя другие настройки конфигурации вместо тех, которые хранятся в \< *имя_проекта*> .configsettings файл. Например, может быть необходимо изменить строку соединения с одним или несколькими источниками данных или задать места хранения для конкретных секций или групп мер.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, необходимо изменить эти данные в \< *имя_проекта*> файл .configsettings, как описано в следующей процедуре. Невозможно изменить настройки секций и ролей в проекте, так как  *\<имя проекта >* **страницы свойств** диалогового окна в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] эти параметры не отображаются.  
  
> [!NOTE]  
>  Настройки конфигурации могут применяться ко всем объектам или только ко вновь созданным объектам. Применяйте параметры конфигурации ко вновь созданным объектам только при развертывании дополнительных объектов в ранее развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , если не нужно перезаписывать существующие объекты. Чтобы указать, параметры конфигурации применяются ко всем объектам или только ко вновь созданным объектам, установите этот параметр в \< *имя_проекта*> .deploymentoptions файл. Дополнительные сведения см. в статье [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md).  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>Изменение настройки конфигурации после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры конфигурации** укажите параметры конфигурации для развертываемых объектов.  
  
     -или-  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -или-  
  
-   Изменить \< *имя_проекта*> .configsettings файл, используя любой текстовый редактор.  
  
## <a name="see-also"></a>См. также  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md)   
 [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
  
