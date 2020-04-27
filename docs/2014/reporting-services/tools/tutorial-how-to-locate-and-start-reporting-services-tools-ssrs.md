---
title: Учебник. Инструкции по поиску и запуску средств служб Reporting Services (SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edd0b6e3928a2bc3a280403a87eda5bb797e620
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099481"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a>Учебник. Инструкции по поиску и запуску средств служб Reporting Services (SSRS)
  В этом учебнике рассказывается о средствах, используемых для настройки сервера отчетов, управления содержимым и операциями сервера отчетов, создания и публикации отчетов. Этот учебник призван помочь новым пользователям понять, как найти и открыть каждый инструмент. Если вы уже знакомы с этими средствами, то можете перейти к другим учебникам, которые помогут научиться правильно использовать службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Дополнительные сведения о других руководствах см. в [руководствах по Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).  
  
 В этом разделе:  
  
-   [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](#bkmk_configuration_manager)  
  
-   [Диспетчер отчетов (собственный режим)](#bkmk_report_manager)  
  
-   [Management Studio](#bkmk_managements_studio)  
  
-   [SQL Server Data Tools с конструктором и мастером отчетов](#bkmk_ssdt)  
  
-   [построитель отчетов](#bkmk_report_builder)  
  
##  <a name="reporting-services-configuration-manager-native-mode"></a><a name="bkmk_configuration_manager"></a>Диспетчер конфигурации служб Reporting Services (собственный режим)  
 Используйте диспетчер конфигурации для работы в собственном режиме, чтобы выполнить следующее:, , , , и.  
  
-   Укажите учетную запись службы.  
  
-   Создайте или обновите базу данных сервера отчетов.  
  
-   Измените свойства соединения.  
  
-   Укажите URL-адреса.  
  
-   Настройте ключи шифрования.  
  
-   Настройте автоматическую обработку отчетов и доставку отчетов по электронной почте.  
  
 **Установка** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] устанавливается одновременно с установкой служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в основном режиме. Дополнительные сведения см. в разделе [Установка сервера отчетов служб Reporting Services в собственном режиме](../install-windows/install-reporting-services-native-mode-report-server.md).  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a>Запуск диспетчера конфигурации служб Reporting Services  
  
1.  На начальном экране Windows введите `reporting` и в результатах поиска **приложений** щелкните **Диспетчер конфигурации служб Reporting Services**.  
  
     ![Диспетчер конфигурации служб Reporting Services после запуска](../media/bi-ssrs-configmanager-win8-startscreen.gif "Диспетчер конфигурации служб Reporting Services после запуска")  
  
     **Ни**  
  
     Нажмите кнопку **Пуск**, выберите пункт **Программы**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Средства настройки**, а затем **Диспетчер конфигурации служб Reporting Services**.  
  
     Появится диалоговое окно **Выбор экземпляра установки сервера отчетов** , в котором можно выбрать настраиваемый экземпляр сервера отчетов.  
  
2.  В поле **Имя сервера**укажите имя компьютера, на котором установлен экземпляр сервера отчетов. По умолчанию указывается имя локального компьютера, но можно ввести имя удаленного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
     Если указан удаленный компьютер, для установления соединения нажмите кнопку **Найти** . Сервер отчетов должен быть заранее настроен для удаленного администрирования. Дополнительные сведения о подготовке сервера отчетов для удаленного администрирования см. в разделе [Настройка сервера отчетов для удаленного администрирования](../report-server/configure-a-report-server-for-remote-administration.md).  
  
3.  В поле **Имя экземпляра** выберите экземпляр служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], который вам нужно настроить. В списке отображаются только экземпляры сервера отчетов [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Более ранние версии служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]настраивать нельзя.  
  
4.  Нажмите кнопку **Соединить**.  
  
5.  Убедиться, что средство запущено, можно, сравнив полученные результаты со следующим изображением:  
  
     ![Средство конфигурации служб Reporting Services](../media/rs-ui-reportserverconfigkatmai.gif "средство настройки служб Reporting Services")  
  
 **Дальнейшие действия:** [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) и [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
##  <a name="report-manager-native-mode"></a><a name="bkmk_report_manager"></a>Диспетчер отчетов (собственный режим)  
 Для установки разрешений, управления подписками и расписаниями, а также работы с отчетами используйте [диспетчер отчетов &#40;служб SSRS в собственном режиме&#41;](../report-manager-ssrs-native-mode.md) . Диспетчер отчетов также можно использовать для просмотра отчетов.  
  
 **Установка:** Диспетчер отчетов устанавливается при установке [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в собственном режиме: [Install Reporting Services сервер отчетов в собственном режиме](../install-windows/install-reporting-services-native-mode-report-server.md)  
  
 Для работы с диспетчером отчетов необходимо иметь соответствующие разрешения (изначально разрешения на доступ к функциональным возможностям диспетчера отчетов имеют только члены группы локальных администраторов). Диспетчер отчетов предоставляет различные страницы и параметры, в зависимости от назначений роли текущего пользователя. Пользователи, у которых нет разрешения, получат пустую страницу. Пользователи, которые имеют разрешения на просмотр отчетов, получат ссылки для открытия отчетов. Дополнительные сведения о разрешениях см. в разделе [Роли и разрешения &#40;службы Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).  
  
#### <a name="to-start-report-manager"></a>Запуск диспетчера отчетов  
  
1.  Откройте браузер. Сведения о поддерживаемых браузерах и версиях браузеров см. в разделе [Планирование поддержки Reporting Services и Power View &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).  
  
2.  В адресной строке веб-браузера введите URL-адрес диспетчера отчетов. URL-адрес по умолчанию **—\<http://servername>/Reports**. Можно использовать программу настройки служб Reporting Services для подтверждения имени сервера и URL-адреса. Дополнительные сведения о URL-адресах, используемых в [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], см. в разделе [Настройка URL-адресов сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
3.  Диспетчер отчетов открывается в окне браузера. Стартовой страницей является корневая папка. В зависимости от разрешений на стартовой странице могут быть видны дополнительные папки, гиперссылки на отчеты и файлы ресурсов. На панели инструментов расположены дополнительные кнопки и команды.  
  
4.  При запуске диспетчер отчетов на локальном сервере отчетов см. раздел [Настройка сервера отчетов в собственном режиме для локального администрирования &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
 **Дальнейшие действия.** [Настройте диспетчер отчетов &#40;основном режиме&#41;](../report-server/configure-web-portal.md).  
  
##  <a name="management-studio"></a><a name="bkmk_managements_studio"></a> Management Studio  
 Администраторы сервера отчетов могут использовать среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для управления сервером отчетов наряду с другими серверными компонентами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).  
  
#### <a name="to-start-sql-server-management-studio"></a>Начало работы в среде SQL Server Management Studio  
  
1.  На начальном экране Windows `sql server` и в результатах поиска **приложений** щелкните **SQL Server Management Studio**.  
  
     ![начальный экран Management Studio на начальном экране Windows](../media/bi-ssms-win8-startscreen.gif "начальный экран Management Studio на начальном экране Windows")  
  
     **Ни**  
  
     Нажмите кнопку **Пуск**, а затем последовательно выберите **Все программы**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]и **SQL Server Management Studio**. Откроется диалоговое окно **Соединение с сервером** .  
  
2.  Если диалоговое окно **Соединение с сервером** отсутствует, то в **обозревателе объектов**нажмите **Подключиться** и выберите **службы Reporting Services**.  
  
3.  В раскрывающемся списке **Тип сервера** выберите **Службы Reporting Services**. Если службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] не находятся на списке, значит, они не установлены.  
  
4.  В раскрывающемся списке **Имя сервера** выберите экземпляр сервера отчетов. В этом списке появятся локальные экземпляры. Можно также ввести имя удаленного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
5.  Нажмите кнопку **Соединить**. Предусмотрена возможность развернуть корневой узел, чтобы задать свойства сервера, изменить определения ролей или отключить те или иные компоненты сервера отчетов.  
  
##  <a name="sql-server-data-tools-with-report-designer-and-report-wizard"></a><a name="bkmk_ssdt"></a>SQL Server Data Tools с конструктор отчетов и мастером отчетов  
 Конструктор отчетов доступен в составе среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] — бизнес-аналитики для Visual Studio 2012. Области конструктора в этом средстве содержат вложенные окна, мастера и меню, используемые для доступа к функциям создания отчетов. Это средство конструктора отчетов становится доступным при выборе шаблона проекта сервера отчетов или мастера сервера отчетов. Дополнительные сведения см. в разделе [Службы Reporting Services в SQL Server Data Tools (SSDT)](reporting-services-in-sql-server-data-tools-ssdt.md).  
  
#### <a name="to-start-report-designer"></a>Запуск конструктора отчетов  
  
1.  На стартовом экране Windows введите **data** и в результатах поиска **Приложения** выберите **SQL Server Data Tools для Visual Studio 2012**.  
  
     **Ни**  
  
     Нажмите кнопку **Пуск**, укажите пункт **все программы**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]а затем выберите пункт **SQL Server Data Tools (SSDT)**.  
  
2.  В меню **Файл** укажите **Создать**, затем нажмите **Проект**.  
  
3.  В списке **Типы проектов** выберите значение **Проекты бизнес-аналитики**.  
  
4.  В списке **Шаблоны** выберите значение **Проект сервера отчетов**. На следующей диаграмме показано, как шаблоны проекта выглядят в диалоговом окне.  
  
     ![Диалоговое окно "Создание шаблона проекта"](../media/rs-ui-newrsproject.gif "Диалоговое окно "Создание шаблона проекта"")  
  
5.  Введите имя и местоположение проекта или нажмите кнопку **Обзор** и выберите местоположение.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)][!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] открывается с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] начальной страницей. В обозревателе решений содержатся категории для создания отчетов и источников данных. Эти категории можно использовать для создания новых отчетов и источников данных. При создании определения отчета появляются окна со вкладками. К окнам со вкладками относятся такие окна, как «Данные», «Макет» и «Предварительный просмотр».  
  
 Чтобы приступить к работе над первым отчетом, см. раздел [Создание простого табличного отчета &#40;учебник по службам SSRS&#41;](../create-a-basic-table-report-ssrs-tutorial.md). Дополнительные сведения о конструкторах запросов, которые можно использовать в конструктор отчетов, см. в разделе [средства проектирования запросов в конструктор отчетов SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).  
  
##  <a name="report-builder"></a>Построитель отчетов <a name="bkmk_report_builder"></a>  
 Используйте [построитель отчетов &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) для создания отчетов в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] разработки, похожей на Office. Можно настраивать и обновлять существующие отчеты, независимо от того, были ли они созданы в конструкторе отчетов или в предыдущих версиях построителя отчетов. Свяжитесь с администратором, чтобы узнать расположение файла ReportBuilder3.msi, который нужно запустить для установки построителя отчетов на локальном компьютере.  
  
 **Установка:** Выбранная версия построителя отчетов устанавливается либо [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в собственном режиме, либо в режиме интеграции с SharePoint. Изолированная версия построителя отчетов доступна как отдельная загрузка.  См. статью [Установка изолированной версии построитель отчетов &#40;построитель отчетов&#41;](../install-windows/install-report-builder.md)  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a>Запуск версии ClickOnce построителя отчетов из диспетчера отчетов (в собственном режиме)  
  
1.  В веб-обозревателе введите URL-адрес диспетчера отчетов для сервера отчетов. URL-адрес по умолчанию —\<http://*ServerName*>/Reports. Откроется диспетчер отчетов.  
  
2.  Щелкните **Построитель отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a>Запуск построителя отчетов ClickOnce с помощью URL-адреса  
  
1.  В адресной строке веб-браузера введите следующий URL-адрес:  
  
     **http://\<ServerName>/репортсервер/репортбуилдер/ReportBuilder_3_0_0_0. Application**  
  
2.  Нажмите клавишу ВВОД.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a>Запуск построителя отчетов ClickOnce в службах Reporting Services в режиме интеграции с SharePoint  
  
1.  Перейдите на сайт, содержащий библиотеку, в которой необходимо создать новый отчет.  
  
2.  Откройте библиотеку.  
  
3.  В меню **Создать** выберите пункт **Отчет в построителе отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
#### <a name="to-start-report-builder-stand-alone"></a>Запуск изолированной версии построителя отчетов  
  
1.  На стартовом экране Windows введите **report builder** , затем выберите **Построитель отчетов 3.0**.  
  
     **Ни**  
  
     Откройте меню «Пуск», выберите **Все программы**, затем **Построитель отчетов Microsoft SQL Server 2014**.  
  
2.  Щелкните **Построитель отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет.  
  
3.  Для открытия документации по построителю отчетов щелкните **Справка построителя отчетов** .  
  
## <a name="see-also"></a>См. также  
 [Поддержка установки, удаления и построитель отчетов](../install-uninstall-and-report-builder-support.md)   
 [Reporting Services установки в режиме интеграции с SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md)   
 [Сервер отчетов Reporting Services](../reporting-services-report-server.md)   
 [Средства проектирования запросов в конструктор отчетов SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)   
 [Учебники по службам Reporting Services (SSRS)](../reporting-services-tutorials-ssrs.md)  
  
  
