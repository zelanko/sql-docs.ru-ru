---
title: Указание параметров конфигурации для развертывания решения | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075268"
---
# <a name="specifying-configuration-settings-for-solution-deployment"></a>Указание настроек конфигурации для развертывания решения
  Мастер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывания считывает параметры развертывания секций и ролей, которые используются в скрипте развертывания, из \<файла *Project Name*>. configsettings. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при сборке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует параметры конфигурации текущего проекта для создания \< *имени проекта*> файл. configsettings.  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>Просмотр настроек конфигурации для развертывания  
 Ниже приведены параметры конфигурации, которые хранятся в \<файле *Project Name*>. configsettings:  
  
-   **Строки подключения к источникам данных** Это строки подключения для каждого источника данных на основе значений, указанных в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекте. Идентификатор пользователя и пароль всегда удаляются из строки соединения до того, как оставшаяся часть строки сохраняется в этом файле. Однако если мастер развертывания выполняет развертывание непосредственно в экземпляре служб Analysis Services, можно ввести нужный идентификатор пользователя и пароль в мастере, что обеспечит успешную обработку развертываемой базы данных. Эти сведения о соединении не сохраняются в самом скрипте развертывания, если он сохраняется мастером развертывания.  
  
-   **Учетные записи олицетворения** Этот параметр задает имя пользователя, которое [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует для выполнения инструкций в каждом источнике данных. Если учетная запись олицетворения не задана, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют собственную учетную запись входа для запуска инструкций. Если учетной записи входа служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставлены разрешения непосредственно в источнике данных, то все администраторы баз данных во всех базах данных в экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют доступ к источнику данных посредством этой учетной записи входа. Если учетная запись пользователя и пароль указаны, то эти сведения всегда удаляются до того, как данные для олицетворения сохраняются в этом файле. Однако если мастер развертывания выполняет развертывание непосредственно в экземпляре служб Analysis Services, можно ввести нужный идентификатор пользователя и пароль в мастере, что обеспечит успешную обработку развертываемой базы данных. Эти сведения об олицетворении не сохранятся в самом скрипте развертывания, если он сохраняется мастером развертывания.  
  
-   **Файлы журналов ошибок ключа** Этот параметр задает имя файла и путь к файлу журнала ошибок ключа для каждого куба, группы мер, секции и измерения в базе данных.  
  
-   **Места хранения** Этот параметр задает место хранения для каждого куба, группы мер и секции в базе данных. Если для объекта не введено значение, то мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует местоположение по умолчанию для объекта. Например, секции используют местоположение для группы мер, группы мер используют местоположение для куба, а кубы используют местоположение по умолчанию для объектов в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Место хранения может быть локальным путем или путем в формате UNC.  
  
-   **Сервер отчетов** Этот параметр задает расположение сервера отчетов и папки для каждого действия отчета, определенного в каждом кубе базы данных.  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>Изменение настроек конфигурации для развертывания  
 В некоторых случаях может потребоваться развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект, используя параметры конфигурации, \<отличные от параметров, хранящихся в файле *Project Name*>. configsettings. Например, может быть необходимо изменить строку соединения с одним или несколькими источниками данных или задать места хранения для конкретных секций или групп мер.  
  
 Чтобы изменить развертывание секций и ролей в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекте, необходимо изменить эти сведения в файле с \< *именем проекта*>. configsettings, как описано в следующей процедуре. Нельзя изменить параметры секций и ролей в проекте, так как [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] * \<* диалоговое окно **страницы свойств>свойства** в не отображает эти параметры.  
  
> [!NOTE]  
>  Настройки конфигурации могут применяться ко всем объектам или только ко вновь созданным объектам. Применяйте параметры конфигурации ко вновь созданным объектам только при развертывании дополнительных объектов в ранее развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , если не нужно перезаписывать существующие объекты. Чтобы указать, применяются ли параметры конфигурации ко всем объектам или только к вновь созданным, установите этот параметр в \<файле *Project Name*>. deploymentoptions. Дополнительные сведения см. в статье [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md).  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>Изменение настройки конфигурации после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме и на странице **Параметры конфигурации** укажите параметры конфигурации для развертываемых объектов.  
  
     -или-  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -или-  
  
-   \<Измените *имя проекта*>. configsettings с помощью любого текстового редактора.  
  
## <a name="see-also"></a>См. также:  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md)   
 [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
  
