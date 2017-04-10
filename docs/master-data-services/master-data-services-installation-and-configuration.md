---
title: "Установка и настройка Master Data Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 37
---
# Установка и настройка Master Data Services
  В этой статье рассматривается установка [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на компьютере под управлением Windows Server 2012 R2, настройка базы данных и веб-сайта MDS, а также развертывание образцов моделей и данных. Службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) позволяют организациям управлять надежной версией данных.   
   
Общие сведения об упорядочении данных в [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]см. в разделе [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md).     
  
 Сведения о новых функциях [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] см. на странице [Новые возможности Master Data Services (MDS)](../master-data-services/what-s-new-in-master-data-services-mds.md).  
 
Ссылки на видео и другие обучающие ресурсы, которые помогут ознакомиться с [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], см. в разделе [Изучение служб Master Data Services](../master-data-services/learn-sql-server-master-data-services.md). 
  
> **Скачать**  
>-   Чтобы скачать [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], перейдите на сайт  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
>-   Есть учетная запись Azure?  Затем перейдите **[сюда](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** , чтобы запустить виртуальную машину с уже установленным [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  .  
 
> **Не удается создать веб-сайт MDS?**
>>Инструкции по решению этой проблемы см. в этой статье службы поддержки Майкрософт.
[Не удается создать веб-сайт MDS с помощью учетной записи с ограниченными правами доступа в SQL Server 2016](https://aka.ms/mdssupport) 
  
## <a name="installing-master-data-services-and-iis-roles-and-features"></a>Установка служб Master Data Services, а также ролей и компонентов IIS  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно установить с помощью мастера установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]или командной строки.  
  
 **Установка [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с помощью программы установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на компьютере под управлением Windows Server 2012 R2**  
  
1.  Дважды щелкните файл Setup.exe и следуйте инструкциям мастера установки.  
  
2.  На странице [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Выбор компонентов **в разделе** Общие компоненты **выберите**.  
  
     При этом устанавливается [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], сборки, оснастка Windows PowerShell, папки и файлы для веб-приложений и служб.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  Завершите работу мастера установки.  
  
4.  В [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]щелкните значок **Диспетчер серверов** на панели задач **рабочего стола**.  
  
     ![Icon for the Server Manager in Windows Server 2012 taskbar](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Icon for the Server Manager in Windows Server 2012 taskbar")  
  
5.  В **диспетчере серверов**в меню **Управление** выберите пункт **Добавить роли и компоненты** .  
  
     ![In Server Manage, the Add Roles and Features menu command](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "In Server Manage, the Add Roles and Features menu command")  
  
6.  На странице **Тип установки** **мастера добавления ролей и компонентов**примите значение по умолчанию (**Установка ролей или компонентов**) и нажмите кнопку **Далее**.  
  
7.  Установите переключатель в положение **Выберите сервер из пула серверов**, а затем щелкните сервер, на котором установлены службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     ![Server Selection page on the Add Roles and Features Wizard](../master-data-services/media/mds-servermanagerdashboard-addrolesandfeatureswizard-serverselection.png "Server Selection page on the Add Roles and Features Wizard")  
  
8.  В поле **Роли** выберите роли и службы ролей, которые требуются для служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)], а затем нажмите кнопку **Далее**. На рисунках ниже показаны выбранные требуемые роли и службы ролей.  
  
    > [!WARNING]  
    >  Не устанавливайте службу роли "Публикация WebDAV". Публикация WebDAV не совместима с [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
    > [!IMPORTANT]  
    >  **Функция сжатия динамического содержимого** IIS по умолчанию включена. Это позволяет существенно уменьшить размер XML-ответа и количество операций сетевого ввода/вывода, однако использование ЦП увеличивается.  Дополнительные сведения см. в разделе **Улучшенная производительность [CTP 2.0]** in [What's New in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
    |Роли и службы ролей|Роли и службы ролей|  
    |-----------------------------|-----------------------------|  
    |![Common HTTP Features](../master-data-services/media/mds-servermanagerdashboard-commonhttpfeaturesroles.png "Common HTTP Features")|![Health Diagnostics Roles](../master-data-services/media/mds-servermanagerdashboard-healthdiagnosticsroles.png "Health Diagnostics Roles")|  
    |![Performance Roles](../master-data-services/media/mds-servermanagerdashboard-performanceroles.png "Performance Roles")|![Security Roles](../master-data-services/media/mds-servermanagerdashboard-securityroles.png "Security Roles")|  
    |![WebServer Application Development Roles](../master-data-services/media/mds-servermanagerdashboard-webserverapplicationdevelopmentroles.png "WebServer Application Development Roles")|![Management Tools](../master-data-services/media/mds-servermanagerdashboard-managementtoolsroles.png "Management Tools")|  
  
     Список требуемых ролей и служб ролей в разных операционных системах см. в разделе [Требования веб-приложений (службы Master Data Services)](../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
9. В поле **Компоненты** выберите компоненты, которые требуются для служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)], а затем нажмите кнопку **Далее**. На рисунках ниже показаны выбранные требуемые компоненты.  
  
    |Компоненты|Функции|  
    |--------------|--------------|  
    |![Net Framework Features](../master-data-services/media/mds-servermanagerdashboard-netframeworkfeatures.png "Net Framework Features")|![Windows Process Features](../master-data-services/media/mds-servermanagerdashboard-windowsprocessfeatures.png "Windows Process Features")|  
  
     Список требуемых компонентов в разных операционных системах см. в разделе [Требования веб-приложений (службы Master Data Services)](../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
 Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью программы установки см. в разделе [Установка SQL Server 2016 с помощью мастера установки (программа установки)](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
 Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью командной строки см. в разделе [Установка SQL Server 2016 из командной строки](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). При использовании командной строки компонент [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] доступен в виде параметра компонента.  
  
 Краткое описание со ссылками на дополнительные сведения о предварительных задачах перед установкой см. в разделе [Установка служб Master Data Services](../master-data-services/install-windows/install-master-data-services.md).  
  
##  <a name="a-namesetupweba-setting-up-the-database-and-website"></a> Настройка базы данных и веб-сайта  
 **Настройка базы данных и веб-сайта с помощью [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]**  
  
1.  Запустите [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]и щелкните **Настройка базы данных** в области слева.  
  
2.  Щелкните **Создать базу данных**, а затем нажмите кнопку **Далее** в **мастере создания базы данных**.  
  
3.  На странице **Сервер базы данных** выберите значение в поле **Тип проверки подлинности** , а затем нажмите кнопку **Проверить подключение** , чтобы проверить возможность подключения к базе данных с помощью учетных данных, выбранных для типа проверки подлинности.  
  
    > [!NOTE]  
    >  Если выбран тип проверки подлинности **Current User – Integrated Security** , поле **Имя пользователя** доступно только для чтения и содержит имя текущей учетной записи пользователя Windows.  
  
     ![The Database server page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-serverpage.png "The Database server page in the Create Database Wizard")  
  
4.  Введите имя в поле **Имя базы данных** . Если необходимо выбрать параметры сортировки Windows и указать один или несколько доступных параметров, таких как **С учетом регистра**, снимите флажок **Параметры сортировки SQL Server по умолчанию** .  
  
     ![The Database page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-databasepage.png "The Database page in the Create Database Wizard")  
  
     Дополнительные сведения о параметрах сортировки Windows см. в разделе [Имя параметров сортировки Windows (Transact-SQL)](https://msdn.microsoft.com/library/ms188046.aspx).  
  
5.  В поле **Имя пользователя** укажите учетную запись пользователя Windows, который будет суперпользователем по умолчанию для служб Master Data Services. Суперпользователь имеет доступ ко всем функциональным областям и может добавлять, удалять и обновлять все модели.  
  
     ![The Administrator Account page in the Create Database Wizard.](../master-data-services/media/mds-configurationmanager-createdatabasewizard-adminpage.png "The Administrator Account page in the Create Database Wizard.")  
  
6.  Нажмите кнопку **Далее**, чтобы просмотреть сводку параметров для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], а затем нажмите кнопку **Далее** еще раз, чтобы создать базу данных.  
  
     Дополнительные сведения о параметрах, доступных в **мастере создания базы данных**, см. в разделе [Мастер создания базы данных (диспетчер конфигурации служб Master Data Services)](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
7.  На странице "Конфигурация базы данных" в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] нажмите "Выбор базы данных".  
  
8.  Нажмите кнопку **Подключиться**, а затем выберите базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , которая была создана в шаге 6.  
  
     ![Connect to Database dialog box for the Database Configuration page](../master-data-services/media/mds-configurationmanager-selectdatabasebutton-connecttodatabasedialog.png "Connect to Database dialog box for the Database Configuration page")  
  
     Настройка базы данных завершена. На странице **Конфигурация базы данных** теперь приводится экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], к которому установлено подключение, созданная база данных и ее текущая версия.  
  
     ![Database Configuration page in the Configuration Manager shows a completed database setup.](../master-data-services/media/mds-configurationmanager-databaseconfig-completed.png "Database Configuration page in the Configuration Manager shows a completed database setup.")  
  
9. В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]щелкните **Веб-конфигурация** в области слева.  
  
10. В поле со списком **Веб-сайт** выберите элемент **Веб-сайт по умолчанию**, а затем нажмите кнопку **Создать** , чтобы создать веб-приложение.  
  
    > [!NOTE]  
    >  Если выбран элемент **Веб-сайт по умолчанию**, необходимо создать веб-приложение. Если в списке выбран элемент **Создать новый веб-сайт** , приложение создается автоматически.  
  
     ![Web Configuration page in the Configuration Manager](../master-data-services/media/mds-configurationmanager-webconfig.png "Web Configuration page in the Configuration Manager")  
  
11. В разделе **Пул приложений** выполните одно из указанных ниже действий.  
  
    -   Введите имя пользователя, которое вы указали в шаге 5 для **учетной записи администратора**базы данных, введите пароль, а затем нажмите кнопку **ОК**.  
  
         **-ИЛИ-**  
  
    -   Введите другое имя пользователя, пароль, а затем нажмите кнопку "ОК".  
  
         При создании базы данных и веб-приложения необязательно использовать одну и ту же учетную запись.  
  
     ![Create Web Application dialog box, Web Configuration page](../master-data-services/media/mds-configurationmanager-webconfig-createwebapplication.png "Create Web Application dialog box, Web Configuration page")  
  
     Дополнительные сведения о диалоговом окне **Создание веб-приложения** см. в разделе [Диалоговое окно "Создание веб-приложения" (диспетчер конфигурации Master Data Services)](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
12. На странице **Веб-конфигурация** в поле **Веб-приложение** щелкните созданное приложение, а затем в разделе **Связывание приложения с базой данных** нажмите кнопку **Выбрать**.  
  
13. Нажмите кнопку **Подключить**, выберите базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , которую нужно связать в веб-приложением, а затем нажмите кнопку **ОК**.  
  
     Настройка веб-сайта завершена. На странице **Веб-конфигурация** теперь приводится выбранный веб-сайт, созданное веб-приложение и база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], связанная с приложением.  
  
     ![The completed Web site configuration](../master-data-services/media/mds-configurationmanager-webconfig-completed.png "The completed Web site configuration")  
  
     Дополнительные сведения о параметрах на странице "Веб-конфигурация" см. в разделе [Страница "Веб-конфигурация" (диспетчер конфигурации Master Data Services)](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
 Также можно использовать [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] для указания других параметров веб-приложений и служб, связанных с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. К примеру, можно указать, как часто загружаются данные или как часто отправляются сообщения проверки. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
##  <a name="a-namedeploysamplea-deploying-sample-models-and-data"></a> Развертывание образцов моделей и данных  
 В состав  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]входят три перечисленных ниже пакета с образцами моделей.   Эти образцы моделей включают в себя данные. **Расположение по умолчанию для пакетов с образцами моделей: %programfiles%\Microsoft SQL Server\130\Master Data Services\Samples\Packages.**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 Вы можете развернуть эти пакеты с помощью средства MDSModelDeploy. Расположение по умолчанию для средства MDSModelDeploy — *диск*\Program Files\Microsoft SQL Server\ 130\Master Data Services\Configuration.  
  
 Сведения о предварительных требованиях для запуска этого средства см. в разделе [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
 Сведения об изменениях, внесенных в данные для поддержки новых возможностей в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], см. в разделе [Примеры: пакеты развертывания моделей (службы Master Data Services)](../Topic/Samples:%20Model%20Deployment%20Packages%20\(Master%20Data%20Services\).md).  
  
 **Развертывание образцов моделей**  
  
1.  Скопируйте пакеты с образцами моделей в папку *диск*\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
2.  Откройте командную строку администратора и перейдите к файлу MDSModelDeploy.exe, выполнив приведенную ниже команду.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration  
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
  
     ![Command line for deploying the Product sample model](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Command line for deploying the Product sample model")  
  
4.  Чтобы просмотреть образцы моделей, выполните указанные ниже действия.  
  
    1.  Перейдите на настроенный веб-сайт [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . См. раздел [Настройка базы данных и веб-сайта](#SetUpWeb) .  
  
         Адрес веб-сайта — http://*имя сервера*/*веб-приложение*/.  
  
    2.  Выберите модель в поле со списком **Модель** и щелкните **Обозреватель**.  
  
         ![MDS Web site, home page.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "MDS Web site, home page.")  
  
## <a name="next-step"></a>Следующий шаг  
 Создайте модель и сущности для данных. См. разделы [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md) и [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
 Общие сведения об использовании модели и сущностей для создания структуры данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] см. в разделе [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
## <a name="did-this-article-help-you-were-listening"></a>Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии сюда: [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services)  
  
## <a name="see-also"></a>См. также:  
 [База данных служб Master Data Services](../master-data-services/master-data-services-database.md)   
 [Веб-приложение диспетчера основных данных](../master-data-services/master-data-manager-web-application.md)   
 [Страница "Конфигурация базы данных" (диспетчер конфигурации служб Master Data Services)](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Новые возможности Master Data Services (MDS)](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  