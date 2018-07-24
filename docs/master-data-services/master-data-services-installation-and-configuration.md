---
title: Установка и настройка служб Master Data Services | Документы Майкрософт
ms.custom: ''
ms.date: 07/28/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f26803afed7f38e00c87db06e1c3c6398d346b5e
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980486"
---
# <a name="master-data-services-installation-and-configuration"></a>Установка и настройка Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этой статье рассматривается установка [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на компьютере под управлением Windows Server 2012 R2, настройка базы данных и веб-сайта MDS, а также развертывание образцов моделей и данных. Службы[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) позволяют организациям управлять надежной версией данных.   
  
> [!NOTE] 
> [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] можно установить на компьютере Windows 10 при использовании выпуска Developer, который теперь поддерживает [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. 
>>Дополнительные сведения о поддержке операционных систем для различных выпусков [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] см. в разделе [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md). 

Общие сведения об упорядочении данных в [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]см. в разделе [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md).     
  
 Сведения о новых функциях [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] см. на странице [Новые возможности Master Data Services (MDS)](../master-data-services/what-s-new-in-master-data-services-mds.md).  
 
Ссылки на видео и другие обучающие ресурсы, которые помогут ознакомиться с [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], см. в разделе [Изучение служб Master Data Services](../master-data-services/learn-sql-server-master-data-services.md). 
  
> **Загрузить**  
>-   Чтобы скачать [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], перейдите на сайт  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2017-ctp/)**.  
>-   Есть учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)** , чтобы запустить виртуальную машину с уже установленным SQL Server.  
 
> **Не удается создать веб-сайт MDS?**
>>Инструкции по решению этой проблемы см. в этой статье службы поддержки Майкрософт.
[Не удается создать веб-сайт MDS с помощью учетной записи с ограниченными правами доступа в SQL Server 2016](https://aka.ms/mdssupport) 

## <a name="internet-explorer-and-silverlight"></a>Internet Explorer и Silverlight
- При установке [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на компьютер под управлением ОС Windows Server 2012 может понадобиться настроить улучшенную безопасность в Internet Explorer, чтобы разрешить использование скриптов на сайте веб-приложения. Без этого просмотр сайта на серверном компьютере работать не будет.
- Для работы в веб-приложении на клиентском компьютере необходимо установить Silverlight 5. Если требуемая версия Silverlight отсутствует, то при переходе к той части веб-приложения, которая использует Silverlight, программа предложит установить Silverlight. Вы можете установить Silverlight 5 **[с этой веб-страницы](https://www.microsoft.com/silverlight/)**.

## <a name="includessmdsshortmdincludesssmdsshort-mdmd-on-an-azure-virtual-machine"></a>[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на виртуальной машине Azure
По умолчанию при запуске виртуальной машины Azure с уже установленным [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] также устанавливаются [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. 

Далее следует установить службы IIS. См. раздел [Установка и настройка служб IIS](#InstallIIS). 

Если вы хотите внести изменения в установку [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], найдите файл setup.exe в папке по умолчанию `<drive>`:\SQLServer_13.0_Full.
  
## <a name="InstallMDS"></a> Установка служб Master Data Services  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно установить с помощью мастера установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]или командной строки.  
  
 **Установка [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с помощью программы установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на компьютере под управлением Windows Server 2012 R2**  
  
1.  Дважды щелкните файл Setup.exe и следуйте инструкциям мастера установки.  
  
2.  На странице [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Выбор компонентов **в разделе** Общие компоненты **выберите**.  
  
     При этом устанавливается [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], сборки, оснастка Windows PowerShell, папки и файлы для веб-приложений и служб.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  Завершите работу мастера установки.  

## <a name="InstallIIS"></a> Установка и настройка служб IIS
  
1.  В [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]щелкните значок **Диспетчер серверов** на панели задач **рабочего стола**.  
  
     ![Значок диспетчера серверов на панели задач Windows Server 2012](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Значок диспетчера серверов на панели задач Windows Server 2012")  
  
5.  В **диспетчере серверов**в меню **Управление** выберите пункт **Добавить роли и компоненты** .  
   
     ![Команда "Добавить роли и компоненты" в диспетчере серверов](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "Команда \"Добавить роли и компоненты\" в диспетчере серверов")  
  
6.  На странице **Тип установки** **мастера добавления ролей и компонентов**примите значение по умолчанию (**Установка ролей или компонентов**) и нажмите кнопку **Далее**.  
  
7.  Установите переключатель в положение **Выберите сервер из пула серверов**, а затем щелкните сервер, на котором установлены службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     ![mds_AddRolesFeaturesWizard_ServerSelectionPage](../master-data-services/media/mds-addrolesfeatureswizard-serverselectionpage.png) 
  
8. На странице **Роли сервера** щелкните **Веб-сервер** и нажмите кнопку **Далее**. 

   ![mds_AddRolesFeaturesWizard_ServerRolesPage](../master-data-services/media/mds-addrolesfeatureswizard-serverrolespage.png)
   
9. На странице **Компоненты** выберите следующие компоненты и нажмите кнопку **Далее**. Они требуются для [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] в [!INCLUDE[winblue_server_2_md](../includes/winblue-server-2-md.md)].
  
    |Компоненты|Компоненты|  
    |--------------|--------------|  
    |![mds_AddRolesFeaturesWizard_FeaturesPage](../master-data-services/media/mds-addrolesfeatureswizard-featurespage.png)|![mds_AddRolesFeaturesWizard_FeaturesPage_WindowsProcActive](../master-data-services/media/mds-addrolesfeatureswizard-featurespage-windowsprocactive.png)|  

10. В левой панели щелкните **Роль веб-сервера (IIS)**, а затем щелкните **Службы ролей**.
11. На странице **Службы ролей** выберите следующие службы и нажмите кнопку **Далее**. Они требуются для [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)].

    > [!WARNING]  
    >  Не устанавливайте службу роли "Публикация WebDAV". Публикация WebDAV не совместима с [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     |Службы ролей|Службы ролей|  
    |-----------------------------|-----------------------------|  
    |![mds_AddRolesFeaturesWizard_RoleServicesPage](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage.png)|![mds_AddRolesFeaturesWizard_RoleServicesPage_PerformSecurity](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-performsecurity.png)|  
    |![mds_AddRolesFeaturesWizard_RoleServicesPage_AppDevsection](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-appdevsection.png)|![mds_AddRolesFeaturesWizard_RoleServicesPage_ManageToolssection](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-managetoolssection.png)|  
    |||  
  
     Список требуемых компонентов и служб ролей в разных операционных системах см. в разделе [Требования веб-приложений (службы Master Data Services)](../master-data-services/install-windows/web-application-requirements-master-data-services.md).   
  
 Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью программы установки см. в разделе [Установка SQL Server 2016 с помощью мастера установки (программа установки)](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
 Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью командной строки см. в разделе [Установка SQL Server 2016 из командной строки](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). При использовании командной строки компонент [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] доступен в виде параметра компонента.  
  
 Краткое описание со ссылками на дополнительные сведения о предварительных задачах перед установкой см. в разделе [Установка служб Master Data Services](../master-data-services/install-windows/install-master-data-services.md).  
  
##  <a name="SetUpWeb"></a> Настройка базы данных и веб-сайта  
 **Настройка базы данных и веб-сайта с помощью [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]**  

 
> [!WARNING]  
    >  Необходимо [установить службы IIS](#InstallIIS) перед запуском [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Configuration Manager. В противном случае Configuration Manager выведет ошибку служб IIS и вы не сможете создать веб-приложение [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].  
    
> **Требование браузера**
>>Веб-приложение [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] работает только в Internet Explorer (IE) 9 или более поздней версии. Internet Explorer 8 и более ранние версии, а также Microsoft Edge и Chrome не поддерживаются.    
  
1.  Запустите [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]и щелкните **Настройка базы данных** в области слева.  
  
2.  Щелкните **Создать базу данных**, а затем нажмите кнопку **Далее** в **мастере создания базы данных**.  
  
3.  На странице **Сервер базы данных** выберите значение в поле **Тип проверки подлинности** , а затем нажмите кнопку **Проверить подключение** , чтобы проверить возможность подключения к базе данных с помощью учетных данных, выбранных для типа проверки подлинности. Нажмите кнопку **Далее**.
  
    > [!NOTE]  
    >  Если выбран тип проверки подлинности **Current User – Integrated Security** , поле **Имя пользователя** доступно только для чтения и содержит имя текущей учетной записи пользователя Windows. Если вы используете [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на виртуальной машине Azure, в поле **Имя пользователя** отображается имя виртуальной машины и имя пользователя для учетной записи локального администратора виртуальной машины. 

    ![mds_2016ConfigManager_CreateDatabaseWizard_ServerPage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-serverpage.png)  
  
4.  Введите имя в поле **Имя базы данных** . Если необходимо выбрать параметры сортировки Windows, снимите флажок **Параметры сортировки SQL Server по умолчанию** и укажите один или несколько доступных параметров, например **С учетом регистра**. Нажмите кнопку **Далее**.

    ![mds_2016ConfigManager_CreateDatabaseWizard_DatabasePage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-databasepage.png)  
  
     Дополнительные сведения о параметрах сортировки Windows см. в разделе [Имя параметров сортировки Windows (Transact-SQL)](../t-sql/statements/windows-collation-name-transact-sql.md).  
  
5.  В поле **Имя пользователя** укажите учетную запись пользователя Windows, который будет суперпользователем по умолчанию для служб Master Data Services. Суперпользователь имеет доступ ко всем функциональным областям и может добавлять, удалять и обновлять все модели.  

    ![mds_2016ConfigManager_CreateDatabaseWizard_AdminPage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-adminpage.png)  
  
6.  Нажмите кнопку **Далее** , чтобы просмотреть сводку параметров для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , а затем нажмите кнопку **Далее** еще раз, чтобы создать базу данных. Откроется страница **Ход выполнения и завершение**.

7. После создания и настройки базы данных нажмите кнопку **Готово**.  
  
     Дополнительные сведения о параметрах, доступных в **мастере создания базы данных**, см. в разделе [Мастер создания базы данных (диспетчер конфигурации служб Master Data Services)](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
7.  На странице **Конфигурация базы данных** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] нажмите **Выбор базы данных**.  
  
8.  Нажмите кнопку **Подключиться**, выберите базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], которая была создана в шаге 7, а затем нажмите кнопку **ОК**. 

    ![mds_2016ConfigManager_SelectDatabaseButton_ConnectToDatabaseDialog](../master-data-services/media/mds-2016configmanager-selectdatabasebutton-connecttodatabasedialog.png)  
  
     Настройка базы данных завершена. На странице **Конфигурация базы данных** теперь приводится экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], к которому установлено подключение, созданная база данных и ее текущая версия.  

    ![mds_2016ConfigManager_DatabaseConfig_Completed](../master-data-services/media/mds-2016configmanager-databaseconfig-completed.png)   
  
9. В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]щелкните **Веб-конфигурация** в области слева.  
  
10. В поле со списком **Веб-сайт** выберите элемент **Веб-сайт по умолчанию**, а затем нажмите кнопку **Создать** , чтобы создать веб-приложение.  
  
    > [!NOTE]  
    >  Если выбран элемент **Веб-сайт по умолчанию**, необходимо создать веб-приложение. Если в списке выбран элемент **Создать новый веб-сайт** , приложение создается автоматически.  

     ![mds_2016ConfigManager_WebConfig](../master-data-services/media/mds-2016configmanager-webconfig.png)  
  
11. В разделе **Пул приложений** выполните одно из указанных ниже действий.  
  
    -   Введите имя пользователя, которое вы указали в шаге 5 для **учетной записи администратора**базы данных, введите пароль, а затем нажмите кнопку **ОК**.  
  
         **-ИЛИ-**  
  
    -   Введите другое имя пользователя, пароль, а затем нажмите кнопку "ОК".  
  
         При создании базы данных и веб-приложения необязательно использовать одну и ту же учетную запись.  

        ![mds_2016ConfigManager_WebConfig_CreateWebApplication](../master-data-services/media/mds-2016configmanager-webconfig-createwebapplication.png)   
  
     Дополнительные сведения о диалоговом окне **Создание веб-приложения** см. в разделе [Диалоговое окно "Создание веб-приложения" (диспетчер конфигурации Master Data Services)](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
12. На странице **Веб-конфигурация** в поле **Веб-приложение** щелкните созданное приложение, а затем в разделе **Связывание приложения с базой данных** нажмите кнопку **Выбрать**.  
  
13. Нажмите кнопку **Подключить**, выберите базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , которую нужно связать в веб-приложением, а затем нажмите кнопку **ОК**.  
  
     Настройка веб-сайта завершена. На странице **Веб-конфигурация** теперь приводится выбранный веб-сайт, созданное веб-приложение и база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , связанная с приложением.  

     ![mds_2016ConfigManager_WebConfig_Completed](../master-data-services/media/mds-2016configmanager-webconfig-completed.png)  
 
     
15. Нажмите кнопку **Применить**. Появится сообщение о **завершении настройки**. Нажмите кнопку **ОК** в окне сообщения, чтобы запустить веб-приложение. Адрес веб-сайта — http://*имя сервера*/*веб-приложение*/. 


![mds_2016ConfigurationComplete_MessageBox](../master-data-services/media/mds-2016configurationcomplete-messagebox.png) 
  
     For more information about the settings on the Web Configuration page, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
 Также можно использовать [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] для указания других параметров веб-приложений и служб, связанных с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . К примеру, можно указать, как часто загружаются данные или как часто отправляются сообщения проверки. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
##  <a name="deploySample"></a> Развертывание образцов моделей и данных  
 В состав  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]входят три перечисленных ниже пакета с образцами моделей.   Эти образцы моделей включают в себя данные. **Расположение по умолчанию для пакетов с образцами моделей: %programfiles%\Microsoft SQL Server\140\Master Data Services\Samples\Packages.**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 Вы можете развернуть эти пакеты с помощью средства MDSModelDeploy. Расположение по умолчанию для средства MDSModelDeploy — *диск*\Program Files\Microsoft SQL Server\ 140\Master Data Services\Configuration.  
  
 Сведения о предварительных требованиях для запуска этого средства см. в разделе [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
 Сведения об изменениях, внесенных в данные для поддержки новых возможностей в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], см. в разделе [Примеры SQL Server: пакеты развертывания моделей (службы Master Data Services)](../master-data-services/sql-server-samples-model-deployment-packages-mds.md).  
  
 **Развертывание образцов моделей**  
  
1.  Скопируйте пакеты с образцами моделей в папку *диск*\Program Files\Microsoft SQL Server\140\Master Data Services\Configuration.  
  
2.  Откройте командную строку администратора и перейдите к файлу MDSModelDeploy.exe, выполнив приведенную ниже команду.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\140\Master Data Services\Configuration  
    ```  
  
3.  Разверните каждый из образцов модели в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , выполнив каждую из приведенных ниже команд.  
  
    > [!IMPORTANT]  
    >  В примерах ниже указывается значение службы `MDS1` . Это значение используется, если при настройке веб-сайта  **было выбрано значение** Веб-сайт по умолчанию [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  См. раздел [Настройка базы данных и веб-сайта](#SetUpWeb) .  
    >   
    >  Если вы создали новый веб-сайт или выбрали другой существующий веб-сайт, сначала выполните приведенную ниже команду, чтобы определить правильное значение службы.  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  Для развертывания модели указывается первое значение службы из списка возвращенных значений.  
    >
    > [!NOTE]
    > Дополнительные сведения о метаданных образцов моделей см. в файле сведений в расположении "c:\Program Files\Microsoft SQL Server\140\Master Data Services\Configuration".
    >
   
     **Развертывание образца модели chartofaccounts_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model ChartofAccounts -service MDS1  
    ```  
  
     **Развертывание образца модели customer_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **Развертывание образца модели product_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Product -service MDS1  
  
    ```  
  
     После успешного развертывания модели появляется сообщение **Работа MDSModelDeploy завершена** .  
  
     На рисунке ниже показана команда для развертывания образца модели product_en.pkg.  
  
     ![Командная строка для развертывания образца модели "Продукт"](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Командная строка для развертывания образца модели \"Продукт\"")  
  
4.  Чтобы просмотреть образцы моделей, выполните указанные ниже действия.  
  
    1.  Перейдите на настроенный веб-сайт [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . См. раздел [Настройка базы данных и веб-сайта](#SetUpWeb) .  
  
         Адрес веб-сайта — http://*имя сервера*/*веб-приложение*/.  
  
    2.  Выберите модель в поле со списком **Модель** и щелкните **Обозреватель**.  
  
         ![Веб-сайт MDS, домашняя страница.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "Веб-сайт MDS, домашняя страница.")  
  
## <a name="next-step"></a>Следующий шаг  
 Создайте модель и сущности для данных. См. разделы [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md) и [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
 Общие сведения об использовании модели и сущностей для создания структуры данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] см. в разделе [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
    
## <a name="see-also"></a>См. также:  
 [База данных служб Master Data Services](../master-data-services/master-data-services-database.md)   
 [Веб-приложение диспетчера основных данных](../master-data-services/master-data-manager-web-application.md)   
 [Страница "Конфигурация базы данных" (диспетчер конфигурации служб Master Data Services)](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Новые возможности Master Data Services (MDS)](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  
