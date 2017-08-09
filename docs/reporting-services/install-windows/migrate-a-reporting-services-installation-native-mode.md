---
title: "Перенос установки служб Reporting Services (Native Mode) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manual Reporting Services migrations
- Report Server Windows service
- custom Reporting Services installations
- automatic Reporting Services migrations
- Reporting Services, upgrades
- upgrading Reporting Services
- migrating Reporting Services
ms.assetid: a6fc56c1-c504-438d-a2b0-5ed29c24e7d6
caps.latest.revision: 54
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b1e79ca61f1de78ca82cb65aadccd9ea214090a7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="migrate-a-reporting-services-installation-native-mode"></a>Перенос установки служб Reporting Services (собственный режим)

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)]

В этом разделе содержатся пошаговые инструкции по переносу одним из следующих поддерживаемых версий [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] развертывание собственного режима в новый экземпляр SQL Server Reporting Services:  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  

Сведения о переносе установки в режиме интеграции с [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
 Миграция определяется как перемещение файлов данных приложений к новому экземпляру SQL Server. Ниже приведены обычные причины, по которым может потребоваться перенести установку.  
  
-   Имеется крупномасштабное развертывание, или требуется увеличение временных показателей работоспособности.  
  
-   Изменяется оборудование или топология установки.  
  
-   Обнаруживается проблема, блокирующая обновление.

## <a name="bkmk_nativemode_migration_overview"></a> Обзор миграции в собственном режиме

 Процесс миграции для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] состоит из шагов, выполняемых вручную и автоматически. При выполнении миграции сервера отчетов выполняются следующие задачи.  
  
-   Создайте резервные копии базы данных, приложения и файлов конфигурации.  
  
-   Выполните резервное копирование ключа шифрования.  
  
-   Установите новый экземпляр SQL Server. Если используется такое же оборудование, можно установить SQL Server side-by-side с существующей установкой, если она была одной из поддерживаемых версий.  
  
    > [!TIP]  
    >  Для установки side-by-side может потребоваться установка SQL Server как именованный экземпляр.  
  
-   Переместите базу данных сервера отчетов и другие файлы приложения с существующего экземпляра новой установки SQL Server.  
  
-   Переместите любые пользовательские файлы приложения в новый экземпляр.  
  
-   Настройка сервера отчетов.  
  
-   Измените файл **RSReportServer.config** , чтобы включить пользовательские параметры с предыдущего экземпляра.  
  
-   Можно также настроить списки управления доступом (ACL) для новой группы служб Windows [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   После проверки работоспособности нового экземпляра удалите неиспользуемые приложения и средства.  
  
 Установлены ограничения на выпуски [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на которых размещается база данных сервера отчетов. Ознакомьтесь со следующим разделом, если повторно используется база данных сервера отчетов, которая была создана в предыдущей установке.  
  
-   [Создать базу данных сервера отчетов](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
##  <a name="bkmk_fixed_database_name"></a> Фиксированное имя базы данных  
 Нельзя переименовать базу данных сервера отчетов. Идентификатор базы данных записывается в хранимых процедурах сервера отчетов при создании базы данных. Переименование первичной или временной баз данных сервера отчетов приводит к возникновению ошибок при выполнении этих процедур, поэтому установка сервера отчетов становится недействительной.  
  
 Если имя базы данных из существующей установки не подходит для новой установки, рассмотрите возможность создания новой базы данных с тем же именем, затем загрузки данных существующего приложения с использованием методов из следующего списка:  
  
-   Запишите [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] скрипт, который вызывает методы SOAP веб-службы сервера отчетов, чтобы копировать данные между базами данных. Можно использовать служебную программу RS.exe для выполнения скрипта. Дополнительные сведения об этом подходе см. в статье [Сценарии и PowerShell со службами Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md).  
  
-   Запишите код, который вызывает поставщика инструментария WMI, чтобы копировать данные между базами данных. Дополнительные сведения об этом подходе см. в статье [Доступ к поставщику WMI для служб Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  
  
-   Если число элементов невелико, можно переиздать отчеты, модели отчетов и общие источники данных из конструктора отчетов, конструктора моделей и построителя отчетов на новом сервере отчетов. Необходимо создать повторно назначения ролей, подписки, общие расписания, расписания моментальных снимков отчета, пользовательские свойства, установленные для отчетов или других элементов, безопасность элементов модели и свойства, назначенные на сервере отчетов. Будут потеряны журнал отчетов и данные журнала выполнения отчета.  
  
##  <a name="bkmk_before_you_start"></a> Перед началом работы  
 Несмотря на то что выполняется миграция, а не обновление экземпляра, попробуйте запустить помощник по обновлению на существующем экземпляре, который поможет обнаружить любые неполадки, влияющие на миграцию. Этот шаг особенно полезен, если выполняется миграция сервера отчетов, установленного и настроенного другим лицом. Запустив помощник по обновлению, то можно узнать о особые параметры, которые могут не поддерживаться в новую установку SQL Server.  
  
 Кроме того необходимо помнить о нескольких важных изменениях в SQL Server Reporting Services, которые влияют на способ миграции установки.
 
- Новый [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] заменил собой диспетчер отчетов.
  
- Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], службы IIS больше не нужны. При переносе экземпляра сервера отчетов на новый компьютер не обязательно добавлять роль веб-сервера. Кроме того, шаги для настройки URL-адресов и проверки подлинности отличаются от предыдущей версии, как и методы и средства диагностики и устранения проблем.  
  
- Веб-служба сервера отчетов, [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]и служба сервера отчетов Windows выполняются под одной учетной записью. Все три приложения считывают параметры конфигурации из файла RSReportServer.config. 
  
- [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] и среда SQL Server Management Studio разработаны таким образом, чтобы устранить перекрытие функций. Каждое средство поддерживает отдельный набор задач.
  
- Фильтры ISAPI не поддерживаются в службах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и более поздних версиях. Если используются фильтры ISAPI, необходимо до осуществления миграции перепроектировать решения по созданию отчетов.  
  
- Ограничения на IP-адреса не поддерживаются в службах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и более поздних версиях. В случае применения ограничений на IP-адреса необходимо до осуществления миграции перепроектировать решения по созданию отчетов либо воспользоваться такой технологией, как брандмауэр, маршрутизатор или преобразование сетевых адресов (NAT) с целью настройки адресов, на которые наложены ограничения по доступу к серверу отчетов.  
  
- Клиентские SSL-сертификаты в службах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и более поздних версиях не поддерживаются. Если используются клиентские SSL-сертификаты, необходимо до осуществления миграции перепроектировать решения по созданию отчетов.  
  
- Если используется тип проверки подлинности, отличный от интегрированной проверки подлинности Windows, необходимо обновить элемент `<AuthenticationTypes>` в файле **RSReportServer.config** с учетом поддерживаемого типа проверки подлинности. К поддерживаемым типам проверки подлинности относятся NTLM, Kerberos, Negotiate и Basic. Такие методы проверки подлинности, как анонимный доступ, дайджест-проверка подлинности и .NET Passport, в службах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и более поздних версиях не поддерживаются.  
  
- Если в среде подготовки отчетов применяются пользовательские каскадные таблицы стилей, они не подлежат переносу. Их нужно перемещать вручную по завершении миграции.  
  
Дополнительные сведения об изменениях в SQL Server Reporting Services см. в документации помощника по обновлению и [новые возможности служб Reporting Services](../../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).  

## <a name="bkmk_backup"></a> Резервное копирование файлов и данных

 Перед установкой нового экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]не забудьте создать резервные копии всех файлов из текущего экземпляра.  
  
1.  Создайте резервную копию ключа шифрования для базы данных сервера отчетов. Этот шаг важен для успешной миграции. На дальнейших этапах процесса миграции необходимо восстановить его для сервера отчетов, чтобы снова получить доступ к зашифрованным данным. Чтобы создать резервную копию ключа, используйте диспетчер настройки служб Reporting Services.  
  
2.  создайте резервную копию базы данных сервера отчетов с помощью любого из поддерживаемых методов резервного копирования базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в инструкциях по созданию резервных копий сервера отчетов базы данных в статье [Перемещение баз данных сервера отчетов на другой компьютер (собственный режим служб SSRS)](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
3.  Создайте резервную копию файлов конфигурации сервера отчетов. Необходимо создать резервные копии следующих файлов:  
  
    1.  RSReportServer.config  
  
    2.  Rswebapplication.config;  
  
    3.  Rssvrpolicy.config  
  
    4.  Rsmgrpolicy.config;  
  
    5.  Reportingservicesservice.exe.config;  
  
    6.  Файл Web.config для сервера отчетов [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] приложения.  
  
    7.  Machine.config — для [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] , если он изменен для операций сервера отчетов.  

## <a name="bkmk_install_ssrs"></a> Установите службы SQL Server Reporting Services

 Установите новый экземпляр сервера отчетов в режиме «Только файлы», чтобы настроить его на использование значений, отличных от выбираемых по умолчанию. Для установки из командной строки используйте аргумент **FilesOnly** . В мастере установки выберите параметр **Установить, но не настраивать сервер**.  
  
 Перейдите по одной из следующих ссылок для просмотра инструкций по установке нового экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   [Установка SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)  
  
-   [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  

## <a name="bkmk_move_database"></a> Перемещение базы данных сервера отчетов

 База данных сервера отчетов содержит опубликованные отчеты, модели отчетов, общие источники данных, расписания, ресурсы, подписки и папки. Она также содержит свойства системы и элемента и разрешения для доступа к содержимому сервера отчетов.  
  
 Если в процессе миграции используется другой экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , необходимо переместить базу данных сервера отчетов в новый экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Если используется тот же экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , перейдите к разделу [Перемещение пользовательских сборок и расширений](#bkmk_move_custom).  
  
 Чтобы переместить базу данных сервера отчетов, выполните следующие действия.  
  
1.  Выберите экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] для использования. SQL Server Reporting Services необходимо использовать один из следующих версий для размещения базы данных сервера отчетов:  
  
    -   SQL Server 2016  
  
    -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
    -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
    -   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
    -   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
2.  Запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и подключитесь к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
3.  Создайте роль **RSExecRole** в системных базах данных, если на компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)] никогда не размещалась база данных сервера отчетов. Дополнительные сведения см. в разделе [Создание RSExecRole](../../reporting-services/security/create-the-rsexecrole.md).  
  
4.  Инструкции см. в статье [Перемещение баз данных сервера отчетов на другой компьютер (собственный режим служб SSRS)](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
 Помните, что база данных сервера отчетов и временная база данных взаимозависимы, поэтому перемещать их необходимо вместе. Не копируйте базы данных. В процессе копирования в новый экземпляр переносятся не все параметры настройки безопасности. Не перемещайте задания агента SQL Server для запланированных операций сервера отчетов. Сервер отчетов автоматически создаст эти задания повторно.  

## <a name="bkmk_move_custom"></a> Перемещение пользовательских сборок и расширений

 Если в установку входят пользовательские элементы отчета, сборки или расширения, необходимо заново разместить пользовательские компоненты. Если пользовательские компоненты не используются, пропустите подраздел [Настройка сервера отчетов](#bkmk_configure_reportserver).  
  
 Для повторного размещения пользовательских компонентов выполните следующее.  
  
1.  Определите, поддерживаются ли сборки или необходима повторная компиляция.

    -  Настраиваемые модули безопасности должны быть повторно написаны с использованием интерфейса [IAuthenticationExtension2](https://msdn.microsoft.com/library/microsoft.reportingservices.interfaces.iauthenticationextension2.aspx) .
  
    -   Пользовательские модули подготовки отчетов для служб [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны быть переписаны с использованием объектной модели для подготовки отчетов (ROM).  
  
    -   Модули подготовки отчетов веб-компонентов Office, использующие HTML 3.2 и HTML OWC, не поддерживаются в службах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и более поздних версиях.  
  
    -   Повторная компиляция других пользовательских сборок необязательна.  
  
2.  Переместите сборки в новую папку \bin сервера отчетов. В SQL Server двоичные файлы сервера отчетов находятся в следующем каталоге для экземпляра сервера отчетов по умолчанию:  
  
     `\Program files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer\bin`  
  
3.  Измените файлы конфигурации, чтобы добавить элементы для пользовательского компонента. Элементы будут зависеть от вида используемой сборки. Инструкции по выбору места размещения файлов и добавлению элементов конфигурации см. в следующих ресурсах:  
  
    1.  [Развертывание пользовательской сборки](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md)  
  
    2.  [Развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
    3.  [Развертывание модуля обработки данных](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
  
    4.  [Развертывание модуля доставки](../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
  
    5.  [Развертывание модуля подготовки отчетов](../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
    6.  [Реализация модуля безопасности](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)  

## <a name="bkmk_configure_reportserver"></a> Настройка сервера отчетов

 Настройте URL-адреса отчета сервера веб-службы и веб-портале и настройте подключение к базе данных сервера отчетов.  
  
 При осуществлении миграции масштабного развертывания нужно перевести в режим «вне сети» все узлы сервера отчетов и перемещать все серверы по одному. После переноса первого сервера отчетов и его успешного подключения к базе данных сервера отчетов, версия базы данных сервера отчетов автоматически обновляется до версии базы данных SQL Server.  
  
> [!IMPORTANT]  
>  Если какие-либо серверы отчетов масштабного развертывания функционируют в режиме «вне сети» и не были подвергнуты переносу, они могут обнаружить исключение rsInvalidReportServerDatabase, поскольку при подключении к обновленным базам данных эти серверы используют более старую схему.  
  
> [!NOTE]  
>  Если при перенесении сервера отчетов он был настроен в качестве общей базы данных для масштабного развертывания, то перед началом настройки службы сервера отчетов необходимо удалить все старые ключи шифрования из таблицы **Keys** в базе данных **ReportServer** . Если ключи не удалить, то сервер отчетов после переноса попытается инициализироваться в режиме масштабного развертывания. Дополнительные сведения см. в статьях [Добавление и удаление ключей шифрования для масштабного развертывания (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) и [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md).  
>   
>  Ключи масштабного развертывания нельзя удалить с помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Старые ключи из таблицы **Keys** в базе данных **ReportServer** необходимо удалить с помощью среды SQL Server Management Studio. Удалите все строки из таблицы Keys. При этом будет выполнена очистка таблицы и ее подготовка для восстановления симметричного ключа, как описано далее.  
>   
>  До удаления ключей рекомендуется сначала создать резервную копию симметричных ключей шифрования. Это можно сделать с помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Откройте диспетчер конфигурации, перейдите на вкладку **Ключи шифрования** и нажмите кнопку **Резервное копирование** . Можно также создать скрипт с командами WMI для резервного копирования ключа шифрования. Дополнительные сведения о WMI см. в статье [Метод BackupEncryptionKey (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-backupencryptionkey.md).  
  
1.  Запустите диспетчер настройки служб Reporting Services и подключитесь к только что установленному экземпляру служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в разделе [Диспетчер конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Настройте URL-адреса для сервера отчетов и веб-портале. Дополнительные сведения см. в статье [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
3.  Настройте базу данных сервера отчетов, выбрав существующую базу данных сервера отчетов из предыдущего экземпляра. После успешной настройки службы сервера отчетов будут перезапущены, и после подключения к базе данных сервера отчетов базы данных автоматически обновляется до SQL Server Reporting Services. Дополнительные сведения о том, как запустить мастер изменения базы данных, который используется для создания или выбора базы данных сервера отчетов см. в разделе [создания собственного отчета сервера базы данных в режиме](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
4.  Восстановите ключи шифрования. Этот шаг необходим, чтобы задействовать обратимое шифрование на предыдущих строках соединения и учетных данных, которые уже находятся в базе данных сервера отчетов. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
5.  Если сервер отчетов установлен на новом компьютере и используется брандмауэр Windows, убедитесь, что порт, который прослушивает сервер отчетов, открыт. По умолчанию для этой цели используется порт 80. Дополнительные сведения см. в статье [Настройка брандмауэра для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
6.  В собственном режиме локального администрирования сервера отчетов, необходимо настроить операционную систему, чтобы разрешить локальное администрирование с веб-портала. Дополнительные сведения см. в разделе [настроить сервер отчетов в собственном режиме для локального администрирования](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  

## <a name="bkmk_copy_custom_config"></a> Копирование настроек пользовательской конфигурации в файл RSReportServer.config

Если изменен файл RSReportServer.config или RSWebApplication.config в предыдущей установке, следует внести те же изменения в новый файл RSReportServer.config. В следующем списке перечислены некоторые из причин изменения предыдущего файла конфигурации и ссылки на дополнительные сведения о способах настройки этих же параметров в SQL Server 2016.  
  
|Пользовательская настройка|Сведения|  
|-------------------|-----------------|  
|Доставка электронной почты сервера отчетов с пользовательскими параметрами|[Настройка почты - службы Reporting Services в собственном режиме](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).|  
|Настройки сведений об устройстве|[Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)|

## <a name="bkmk_windowsservice_group"></a> Группа служб Windows и списки управления доступом

 В [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], имеется одна группа служб, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] группа служб Windows, который используется для создания безопасности списки управления доступом для разделов реестра, файлов и папок, устанавливаемых со службами SQL Server Reporting Services. Это имя группы Windows отображается в формате SQLServerReportServerUser$\<*имя_компьютера*>$\<*имя_экземпляра*>.  

## <a name="bkmk_verify"></a> Проверка развертывания

1.  Проверьте виртуальные каталоги сервера отчетов и [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] , открыв браузер и введя URL-адрес. Дополнительные сведения см. в статье [Проверка установки служб Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).  
  
2.  Проверьте отчеты и убедитесь в том, что они содержат ожидаемые данные. Просмотрите сведения об источнике данных на предмет того, содержатся ли в них данные о подключении к источнику данных. Сервер отчетов использует объектную модель отчета при обработке и подготовке отчетов к просмотру, но не заменяет [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] конструкций с новыми элементами языка определения отчетов. Для получения дополнительных сведений о существующих отчетов запустите на новую версию сервера отчетов, в разделе [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  

## <a name="bkmk_remove_unused"></a> Удаление неиспользуемых программ и файлов

После успешного переноса сервера отчетов на новый экземпляр, можно выполнить следующие действия для удаления программы и файлы, которые более не нужны.  
  
1.  Удалите прежнюю версию служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , если она больше не нужна. Этот шаг не удаляет следующие элементы, но их можно удалить вручную, если они больше не нужны:  
  
    -   старую базу данных сервера отчетов;  
  
    -   роль RsExec;  
  
    -   учетную запись службы сервера отчетов;  
  
    -   пул приложений для веб-службы сервера отчетов;  
  
    -   виртуальные каталоги для диспетчера отчетов и сервера отчетов;  
  
    -   файлы журналов сервера отчетов.  
  
2.  Удалите службы IIS, если они более не нужны на этом компьютере.

## <a name="next-steps"></a>Следующие шаги

[Перенос установки служб Reporting Services](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)   
[База данных сервера отчетов](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
[Обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[Обратная совместимость служб отчетов](../../reporting-services/reporting-services-backward-compatibility.md)   
[Диспетчер конфигурации служб Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
