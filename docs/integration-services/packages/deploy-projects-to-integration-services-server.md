---
title: "Развертывание проектов на сервере служб Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9402f4-4d50-49ff-820d-65a77829c4a5
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Развертывание проектов на сервере служб Integration Services
  В текущей версии служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]вы можете развертывать проекты на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Сервер служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет управлять пакетами, выполнять пакеты и настраивать значения времени выполнения для пакетов с помощью сред.  
  
 Дополнительные сведения о средах см. в разделе [Создание и сопоставление серверной среды](../../integration-services/packages/create-and-map-a-server-environment.md).  
  
> [!NOTE]  
>  Как и в более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], в текущем выпуске можно также развертывать пакеты на экземпляре SQL Server, кроме того, запускать пакеты и управлять ими с помощью служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Использование модели развертывания пакетов. Дополнительные сведения см. в разделе [Устаревшее развертывание пакетов (службы SSIS)](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
 Для развертывания проекта на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] необходимо выполнить следующие задачи.  
  
1.  Создайте каталог SSISDB, если он еще не создан. Дополнительные сведения см. в разделе [Создание каталога служб SSIS](../../integration-services/service/create-the-ssis-catalog.md).  
  
2.  **Мастер преобразования проекта служб Integration Services** преобразует проект в модель развертывания проекта. Дополнительные сведения см. в инструкциях ниже: [Преобразование проекта в модель развертывания проекта](#convert)  
  
    -   При создании проекта в службах [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]по умолчанию проект использует модель развертывания проекта.  
  
    -   Если проект был создан в более раннем выпуске служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], то после открытия файла проекта в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]необходимо преобразовать проект в модель развертывания проекта.  
  
        > [!NOTE]  
        >  Если проект содержит один или более источников данных, то они будут удалены после завершения преобразования проекта. Для создания соединения с источником данных, который может совместно использоваться пакетами в проекте, добавьте диспетчер соединений на уровне проекта. Дополнительные сведения см. в статье [Add, Delete, or Share a Connection Manager in a Package](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
         В зависимости от того, запускается ли **Мастер преобразования проекта служб Integration Services** из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], он выполняет разные задачи по преобразованию.  
  
        -   Если мастер запускается из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], пакеты, содержащиеся в проекте, преобразовываются из [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 2005, 2008 или 2008 R2 в формат, который используется текущей версией служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Исходные файлы проекта (DTPROJ) и пакета (DTSX) обновляются.  
  
        -   Если мастер запускается из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], мастер формирует файл развертывания проекта (ISPAC) из пакетов и конфигураций, содержащихся в проекте. Исходные файлы пакета (DTSX) не обновляются.  
  
             На странице **Выбор назначения** мастера вы можете создать или выбрать существующий файл.  
  
             Чтобы обновить файлы пакета при преобразовании проекта, запустите **Мастер преобразования проекта служб Integration Services** из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Чтобы обновить файлы пакета, не выполняя преобразование проекта, запустите из среды ** ** Мастер преобразования проектов служб Integration Services [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем **Мастер обновления пакетов служб SSIS**. Если выполняется только обновление файлов пакета, следует убедиться в том, что внесенные изменения сохранены. В противном случае при преобразовании проекта в модель развертывания проекта несохраненные изменения в пакете преобразованы не будут.  
  
     Дополнительные сведения об обновлении пакетов см. в разделах [Обновление пакетов служб Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md) и [Обновление пакетов служб Integration Services с помощью мастера обновления пакетов служб SSIS](../../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
3.  Разверните проект на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Дополнительные сведения см. в инструкциях ниже: [Развертывание проекта на сервере служб Integration Services](#deploy).  
  
4.  (Необязательно.) Создайте среду для развернутого проекта. Дополнительные сведения см. в статье [Создание и сопоставление серверной среды](../../integration-services/packages/create-and-map-a-server-environment.md).  
  
##  <a name="convert"></a> Преобразование проекта в модель развертывания проекта  
  
1.  Откройте проект в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], а затем в обозревателе решений щелкните его правой кнопкой мыши и выберите команду **Преобразовать в модель развертывания проекта**.  
  
     -или-  
  
     В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] в обозревателе объектов щелкните правой кнопкой мыши узел **Проекты** и выберите команду **Импорт пакетов**.  
  
2.  Завершите работу мастера. Дополнительные сведения см. в статье [Integration Services Project Conversion Wizard](../../integration-services/packages/integration-services-project-conversion-wizard.md).  
  
##  <a name="deploy"></a> Развертывание проекта на сервере служб Integration Services  
  
1.  Откройте проект в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], а затем из меню **Проект** выберите пункт **Развернуть** , чтобы запустить **Мастер развертывания служб Integration Services**.  
  
     -или-  
  
     В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] разверните узел [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] > **SSISDB** в обозревателе объектов и найдите папку "Проекты" для того проекта, который требуется развернуть. Щелкните папку **Проекты** правой кнопкой мыши и выберите команду **Развернуть проект**.  
  
     -или-  
  
     Из командной строки запустите **isdeploymentwizard.exe**, расположенный в каталоге **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**. На 64-разрядных компьютерах есть также 32-разрядная версия средства в каталоге **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**.  
  
2.  Чтобы выбрать файл развертывания для проекта, на странице **Выбор источника** щелкните **Файл развертывания проекта** .  
  
     -ИЛИ-  
  
     Щелкните **Каталог служб Integration Services** , чтобы выбрать проект, который уже был развернут в каталог служб SSISDB.  
  
3.  Завершите работу мастера. Дополнительные сведения см. в статье [Integration Services Deployment Wizard](../../integration-services/packages/integration-services-deployment-wizard.md).  
  
  