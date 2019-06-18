---
title: Устранение неполадок при установке служб Reporting Services | Документы Майкрософт
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6a36d9acd795bfbcc226d7ffe601fd2b15ee7406
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65502669"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Устранение неполадок при установке служб Reporting Services

  Если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не удалось установить из-за ошибок, возникших в процессе установки, воспользуйтесь инструкциями, приведенными в этом разделе, чтобы выяснить причины, которые, скорее всего, привели к их возникновению.  
  
 Сведения о других ошибках и проблемах, связанных со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], см. в разделе [Устранение неполадок и ошибок служб SSRS](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx).  
  
 В случае обнаружения проблемы, описанной в заметках о выпуске, см. статью [Заметки о выпуске в Интернете](https://go.microsoft.com/fwlink/?linkid=236893).  
  
##  <a name="bkmk_setuplogs"></a> Проверка журналов установки  
 Ошибки установки записываются в файлы журналов, расположенные в папке **[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Setup Bootstrap\Log** . При каждом запуске программы установки там создается новая вложенная папка. Эта вложенная папка имеет имя, включающее время и дату запуска программы установки. Дополнительные сведения о просмотре файлов журналов установки см. в статье [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
-   Журналы содержат набор файлов.  
  
-   Сведения о продукте, компонентах и экземпляре можно просмотреть в файлах с именем «*_summary.txt».  
  
-   Файлы «*_errorlog.txt» содержат сведения об ошибках, сформированных в процессе установки.  
  
-   Откройте файл *_RS\_\*_ComponentUpdateSetup.log, чтобы просмотреть сведения об установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
##  <a name="bkmk_prereq"></a> Проверка требований, необходимых для установки  
 Программа установки автоматически проверяет требования, необходимые для установки. Однако при устранении неполадок, возникших в процессе установки, бывает полезно знать, на соответствие каким именно требованиям производится проверка.  
  
-   Требования к учетной записи для запуска программы установки включают членство в локальной группе «Администраторы». Программа установки должна иметь разрешения на добавление файлов, параметров реестра, создание локальных групп безопасности и предоставление разрешений. При установке конфигурации по умолчанию программа установки должна иметь разрешения на создание базы данных сервера отчетов на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором выполняется установка.  
  
-   Операционная система должна поддерживать службу HTTP.SYS 1.1.  
  
-   Служба HTTP должна быть включена и запущена.  
  
-   Кроме того, если устанавливается служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должен быть запущен координатор распределенных транзакций (DTC).  
  
-   В папке System32 должна присутствовать библиотека Authz.dll.  
  
 Программа установки больше не проверяет наличие служб IIS или [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требуются компоненты MDAC 2.0 и платформа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] версии 2.0. Если эти компоненты не установлены, то будет произведена их установка.  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
##  <a name="bkmk_tshoot_sharepoint"></a> Устранение неполадок с установкой в режиме интеграции с SharePoint  
  
-   [Диспетчер конфигурации служб Reporting Services не запускается](#bkmk_configmanager_notstart)  
  
-   [После установки служб SQL Server Reporting Services в режиме интеграции с SharePoint службы SQL Server Reporting Services 2016 не отображаются в центре администрирования SharePoint.](#bkmk_no_ssrs_service)  
  
-   [Командлеты PowerShell для служб Reporting Services недоступны, и команды не распознаются.](#bkmk_cmdlets_not_recognized)  
  
-   [Будет выдано сообщение об ошибке, указывающее на то, что не настроен URL-адрес](#bkmk_URL_not_configured)  
  
-   [Программа установки завершает работу с ошибками на компьютере с установленным, но не настроенным компонентом SharePoint](#bkmk_sharepoint_not_confiugred)  
  
-   [Страница центра администрирования SharePoint пуста.](#bkmk_central_admin_blank)  
  
-   [При попытке создать отчет построителя отчетов отображается сообщение об ошибке](#bkmk_reportbuilder_newreport_error)  
  
-   [Отображается сообщение об ошибке: RS_SHP не поддерживается для действия PREPAREIMAGE](#bkmk_RS_SHP_notsupported)  

### <a name="bkmk_configmanager_notstart"></a> Диспетчер конфигурации служб Reporting Services не запускается

 **Описание.** Эта проблема присуща SQL Server 2012 и более поздним версиям. Службы Reporting Services рассчитаны на архитектуру службы SharePoint. Диспетчер конфигурации больше не нужен для настройки и администрирования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме совместимости с SharePoint.  
  
 **Обходное решение.** Для настройки сервера отчетов в режиме Sharepoint используйте центр администрирования SharePoint. Дополнительные сведения см. в статье [Управление служебным приложением SharePoint службы Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_no_ssrs_service"></a> После установки служб SQL Server Reporting Services в режиме интеграции с SharePoint службы SQL Server Reporting Services 2016 не отображаются в центре администрирования SharePoint.  
 **Описание**. Если после успешной установки служб SQL Server 2016 Reporting Services в режиме интеграции с SharePoint и надстроек служб SQL Server 2016 Reporting Services для SharePoint 2013/2016 вы не видите пункт SQL Server Reporting Service в двух следующих меню, то служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не зарегистрирована:  
  
-   Центр администрирования SharePoint 2013/2016 -> Управление приложениями -> Страница "Управление службами на сервере"  
  
-   Центр администрирования SharePoint 2013 или 2016 -> Управление приложениями -> Управление приложениями службы -> меню "Создать"  
  
 **Обходное решение**. Чтобы зарегистрировать и запустить службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint, выполните следующие действия.  
  
1.  На компьютере, где запущен центр администрирования SharePoint 2013/2016  
  
    1.  Откройте консоль управления SharePoint 2013/2016 с разрешениями администратора. Щелкните значок правой кнопкой мыши и выберите **Запуск от имени администратора**. Вызовите на выполнение из командной оболочки следующие три командлета:  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  Убедитесь, что состояние службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на этой странице отображается с меткой **Запущена**: Центр администрирования SharePoint 2013/2016 -> **Управление приложениями** -> **Управление службами на сервере**.  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_cmdlets_not_recognized"></a> Командлеты PowerShell для служб Reporting Services недоступны, и команды не распознаются.  
 **Описание**. При попытке запуска командлета PowerShell [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выводится сообщение об ошибке следующего содержания:  
  
-   Термин "Install-SPRSServiceInstall-SPRSService" **не распознан** как имя командлета, функции, файла скрипта или действующей программы. Проверьте правильность написания имени, а если включен путь, то проверьте правильность пути и повторите попытку. В строке:1 char:39+ Install-SPRSServiceInstall-SPRSService <<<<    + CategoryInfo          : ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **Обходное решение**. Выполните одно из следующих действий:  
  
-   Запустите надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint. **rssharepoint.msi**.  
  
-   Установите службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint с установочного носителя SQL Server.  
  
 Если при выполнении одного из описанных обходных путей открыта **консоль управления SharePoint 2013/2016**, закройте и снова откройте ее.  
  
 Дополнительные сведения см. в следующих статьях:  
  
-   [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Установка первого сервера отчетов в режиме интеграции с SharePoint](install-the-first-report-server-in-sharepoint-mode.md)  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_URL_not_configured"></a> Будет выдано сообщение об ошибке, указывающее на то, что не настроен URL-адрес  
 **Описание**. Будет выдано приблизительно такое сообщение об ошибке:  
  
 Функциональность служб SQL Server Reporting Services (SSRS) не поддерживается. С помощью центра администрирования проверьте и исправьте одну из следующих проблем:
 
 - Не настроен URL-адрес сервера отчетов. Задайте его на странице интеграции со службами SSRS.
 
 - Не задан прокси-сервер для приложения службы SSRS. Настройте прокси-сервер на страницах приложения службы SSRS.
 
 - Приложение службы SSRS не сопоставлено с этим веб-приложением. На страницах приложения службы SSRS можно связать прокси-сервер приложения службы SSRS с группой прокси-серверов приложения для данного веб-приложения. 
  
 **Обходное решение.** Сообщение об ошибке содержит три рекомендованных способа для решения этой проблемы. Первая рекомендация в сообщении "URL-адрес сервера отчетов не настроен". относится к случаю интеграции с версией сервера отчетов до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Конфигурация SharePoint для предыдущих версий сервера отчетов выполнялась на странице **Общие параметры приложения** в службах **SQL Server Reporting Services (2008 и 2008 R2)** .  
  
 **Дополнительные сведения.** Это сообщение будет выдано при попытке обращения к любым функциям служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые потребуют соединения со службой [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . В том числе:  
  
-   Открытие построителя отчетов SQL Server из библиотеки документов SharePoint.  
  
-   Управление подписками.  
  
-   Управление приложением службы.  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a> Программа установки завершает работу с ошибками на компьютере с установленным, но не настроенным компонентом SharePoint  
 **Описание.** Если выбрать установку служб Reporting Services в режиме интеграции с SharePoint на компьютере, где SharePoint установлен, но не настроен, появится сообщение, аналогичное приведенному ниже, а программа установки завершит работу.  
  
 Программа установки SQL Server завершила работу  
  
 **Обходное решение.** Настройте SharePoint, а затем запустите установку SQL Server.  
  
 **Дополнительные сведения.** При установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в существующей установке SharePoint программа установки попытается установить и запустить службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint. Если SharePoint не настроен, установка службы завершится сбоем, в результате чего программа установки также завершится сбоем.  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_central_admin_blank"></a> Страница центра администрирования SharePoint пуста.  
 **Описание.** Установка SharePoint 2013/2016 прошла успешно, без ошибок. Однако при просмотре центра администрирования отображается только пустая страница.  
  
 **Обходное решение.** Эта проблема связана не со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а с глобальной конфигурацией разрешений в установке SharePoint. Вот несколько советов:  
  
-   Просмотрите раздел справки SharePoint по средам разработки. [Настройка общей среды разработки для SharePoint](https://msdn.microsoft.com/library/ee554869)  
  
-   Просмотр сообщения на форуме: [Центр администрирования отображает пустую страницу после установки в Windows 7](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   Учетная запись службы, используемая для служб SharePoint, например службы центра администрирования SharePoint 2013/2016, должна обладать правами администратора в локальной операционной системе.  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a> При попытке создать отчет построителя отчетов отображается сообщение об ошибке  
 **Описание.** При попытке создать отчет построителя отчетов внутри библиотеки документов отображается сообщение об ошибке, похожее на приведенное ниже:  
  
 Эта функция не поддерживается, поскольку приложения служб SQL Server Reporting Services не существует либо в центре администрирования не настроен URL-адрес сервера отчетов.  
  
 **Обходное решение.** Проверьте наличие и правильность настройки приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . См. дополнительные сведения об [установке сервера отчетов в режиме интеграции с SharePoint](install-the-first-report-server-in-sharepoint-mode.md).
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a> Отображается сообщение об ошибке: RS_SHP не поддерживается для действия PREPAREIMAGE  
 **Описание**. При попытке запуска PREPAREIMAGE для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выдается сообщение об ошибке приблизительно такого содержания:  
  
 "Указанный компонент RS_SHP не поддерживается при запуске действия PREPAREIMAGE, поскольку он не поддерживает SysPrep. Удалите компоненты, несовместимые с SysPrep, и запустите программу установки еще раз".  
  
 **Обходное решение**. Решение отсутствует. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не поддерживают SYSPREP (PREPAREIMAGE). [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает SYSPREP.  
  
 ![Значок стрелки, используемый со ссылкой "В начало"](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой \"В начало\"") [Устранение неполадок установки в режиме интеграции с SharePoint](#bkmk_tshoot_sharepoint)  

::: moniker-end
  
##  <a name="bkmk_tshoot_native"></a> Устранение неполадок установки в собственном режиме  
  
###  <a name="PerfCounters"></a> Счетчики производительности невидимы после обновления до Windows Vista или Windows Server 2008  
 Если выполнено обновление операционной системы с переходом к версии [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] или [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] на компьютере, где работают службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], то после обновления счетчики производительности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не будут установлены.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Восстановление счетчиков производительности служб Reporting Services  
  
1.  Удалите следующие разделы реестра:  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2016 Windows Service**  
  
2.  Откройте окно командной строки и введите следующую команду:  
  
    -   **run \<** *каталог .NET 4.0 Framework* **>\InstallUtil.exe \<** *каталог Bin сервера отчетов* **>\ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  Замените строку \<*каталог платформы .NET 4.0 Framework*> обозначением физического пути к файлам платформы .NET Framework 4.0, а строку \<*каталог Bin сервера отчетов*> — обозначением физического пути к исполняемым файлам сервера отчетов.  
  
3.  Перезапустите службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Чтобы убедиться, что данные шаги были выполнены успешно, откройте веб-браузер и перейдите по URL-адресу веб-портала или сервера отчетов. После этого откройте системный монитор, чтобы проверить, работают ли счетчики.  
  
#### <a name="to-add-the-performance-registry-keys-again-by-using-registry-editor"></a>Повторное добавление разделов производительности в реестре при помощи редактора реестра  
  
1.  Откройте редактор реестра следующим образом.  
  
    1.  Нажмите кнопку **Пуск**и выберите пункт **Выполнить**.  
  
    2.  В диалоговом окне **Выполнить** в поле **Открыть** введите **regedit**.  
  
2.  В редакторе реестра выберите следующий раздел реестра: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance`  
  
3.  Щелкните правой кнопкой мыши узел **Performance** , укажите пункт **Создать**, а затем щелкните **Мультистроковый параметр**.  
  
4.  Введите **Counter Names** и нажмите клавишу ВВОД.  
  
5.  Повторите эти шаги для добавления раздела реестра **Counter Types** в этом узле.  
  
6.  Перейдите к следующему разделу реестра: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance`  
  
7.  Щелкните правой кнопкой мыши узел **Performance** , укажите пункт **Создать**, а затем щелкните **Мультистроковый параметр**.  
  
8.  Введите **Counter Names** и нажмите клавишу ВВОД.  
  
9. Повторите эти шаги для добавления раздела реестра **Counter Types** в этом узле.  
  
 После исправления 64-разрядного экземпляра или повторного добавления разделов реестра вручную можно использовать системный монитор для настройки объектов производительности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], которые необходимо мониторить.  
  
###  <a name="ConfigPropsMissing"></a> Свойства настройки ReportServerExternalURL и PassThroughCookies не настраиваются после обновления с переходом от версии SQL Server 2005  
 При обновлении с переходом от [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] к службам [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]свойства конфигурации **ReportServerExternalURL** и **PassThroughCookies** не настраиваются процессом обновления. **ReportServerExternalURL** — это необязательное свойство, и его следует задавать, только если вы используете веб-части SharePoint 2.0, а пользователи должны иметь возможность получить отчет и открыть его в новом окне браузера. Дополнительные сведения о **ReportServerExternalURL** см. в статье [URL-адреса файлов конфигурации (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md). Свойство**PassThroughCookies** необходимо только при использовании нестандартного метода проверки подлинности. Дополнительные сведения о **PassThroughCookies** см. в статье [Настройка передачи файлов cookie для пользовательской проверки подлинности на веб-портале](../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
> [!NOTE]  
>  При использовании нестандартной проверки подлинности рекомендуется произвести миграцию установки, а не выполнять обновление. Дополнительные сведения о переносе [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в статье [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 По умолчанию эти свойства в конфигурации служб [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] не существуют. Если эти свойства настроены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и остается необходимость в предоставляемых ими функциях, необходимо вручную добавить их в файл **RSReportServer.config** после завершения процесса обновления. Дополнительные сведения см. в статье [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  

### <a name="WindowsAuthBreaksAfterUpgrade"></a> При использовании проверки подлинности Windows после обновления с переходом от версии SQL Server 2005 к версии SQL Server 2016 возникает ошибка "401 — нет доступа"

 Если выполнено обновление с переходом от служб [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] к службам [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], а после обновления используется проверка подлинности NTLM при помощи встроенной учетной записи для учетной записи службы сервера отчетов, то во время доступа к серверу отчетов или веб-порталу отчетов может возникнуть ошибка "401 — нет доступа".  
  
 Это происходит вследствие изменения в настройке по умолчанию служб [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] для проверки подлинности Windows. Настроено «Negotiate», если учетной записью службы сервера отчетов является Network Service или Local System. Настроена NTLM, если учетная запись службы сервера отчетов не входит в число этих встроенных учетных записей. Для устранения этой проблемы после обновления можно изменить файл RSReportServer.config и выполнить настройку, чтобы параметр **AuthenticationType** имел значение **RSWindowsNTLM**. Дополнительные сведения см. в статье [Configure Windows Authentication on the Report Server](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).  

### <a name="Uninstall32BitBreaks64Bit"></a> Удаление 32-разрядного экземпляра служб SQL Server 2016 Reporting Services при параллельном развертывании с 64-разрядным экземпляром приводит к нарушению работы 64-разрядного экземпляра

 Параллельная установка на компьютер 32-разрядного и 64-разрядного экземпляров служб [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] и последующее удаление 32-разрядного экземпляра приводит к удалению четырех разделов реестра для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В результате происходит нарушение работы 64-разрядного экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. При удалении 32-разрядного экземпляра удаляются следующие разделы реестра для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Windows Service\Performance:Counter Types`  
  
 Для устранения этой проблемы можно внести исправления в 64-разрядный экземпляр. Безусловно, рекомендуется использовать процесс исправления, но разделы реестра можно вновь добавить вручную при помощи редактора реестра.  
  
> [!CAUTION]  
>  Неправильное изменение реестра может вызвать серьезные проблемы. Перед внесением изменений в реестр рекомендуется создать резервную копию всех важных данных.  
  
##  <a name="bkmk_additional"></a> Дополнительные ресурсы  
 Ниже приведены дополнительные ресурсы, которые могут быть полезны при устранении проблем:  
  
-   Вики-сайт TechNet: [Устранение неполадок служб SQL Server Reporting Services (SSRS) в режиме интеграции с SharePoint 2010](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [Форум: службы SQL Server Reporting Services](https://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
-   У вас есть отзывы или другие вопросы? Посетите сайт [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
  
