---
description: Upgrade and Migrate Reporting Services
title: Обновление и перенос служб Reporting Services | Документы Майкрософт
ms.prod: reporting-services
ms.prod_service: reporting-services-native
helpviewer_keywords:
- SSRS, upgrading
- Reporting Services, upgrades
- SQL Server Reporting Services, upgrading
- upgrading Reporting Services
author: maggiesMSFT
ms.author: maggies
ms.topic: conceptual
ms.date: 05/01/2020
ms.openlocfilehash: f473590243956cd2fcba1961d3580fa052d6f4c1
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91934631"
---
# <a name="upgrade-and-migrate-reporting-services"></a>Upgrade and Migrate Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Этот раздел содержит общие сведения о вариантах обновления и миграции для служб SQL Server Reporting Services. Вот основные подходы к обновлению развертывания служб SQL Server Reporting Services:  
 
- **Обновление *до* Reporting Services 2016 и более ранних версий *с* Reporting Services 2016 и более ранних версий:** Обновляются компоненты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на тех серверах и экземплярах, где они установлены в данный момент. Обычно это называется обновлением на месте. Обновление на месте с одного режима сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на другой режим не поддерживается. Например, невозможно обновить сервер отчетов в собственном режиме до сервера отчетов в режиме интеграции с SharePoint. Элементы отчета можно переносить из одного режима в другой. Дополнительные сведения см. в разделе [Сценарии миграции и обновления в режиме интеграции с SharePoint](#bkmk_sharePoint_scenarios) далее в этом документе.  

- **Обновление *до* Reporting Services 2017 и более поздних версий *с* Reporting Services 2016 и более ранних версий** выполняется не так, как для предыдущих версий. Обновление *до* Reporting Services 2016 и более ранних версий выполняется на месте с помощью установочного носителя SQL Server. При обновлении *до* Reporting Services 2017 и более поздних версий *с* Reporting Services 2016 и более ранних версий вы не сможете выполнить те же действия, так как новая установка Reporting Services является отдельным продуктом. Она больше не входит в установочный носитель SQL Server. 

    Чтобы выполнить обновление с Reporting Services 2016 и более ранних версий до Reporting Services 2017 и более поздних версий, следуйте инструкциям в разделе [Миграция установки Reporting Services (собственный режим)](migrate-a-reporting-services-installation-native-mode.md), выбрав Reporting Services 2017 в качестве целевого экземпляра. 

- **Обновление *с* Reporting Services 2017 до будущих версий** также будет выполняться на месте, так как идентификаторы GUID установки продукта одинаковы. Запустите файл установки SQLServerReportingServices.exe, чтобы начать обновление на месте на сервере, где уже установлен Reporting Services.
  
- **Миграция.** Устанавливается и настраивается новая среда SharePoint, в нее копируются элементы отчетов и ресурсы, а затем выполняется настройка новой среды для использования существующего содержимого. Более низкая форма миграции — копирование баз данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , файлов конфигурации и при использовании режима интеграции с SharePoint баз данных содержимого SharePoint.  


> [!NOTE]
> Интеграция служб Reporting Services с SharePoint недоступна после выхода SQL Server 2016.
   
##  <a name="known-upgrade-issues-and-best-practices"></a><a name="bkmk_known_issues"></a> Известные проблемы и рекомендации, связанные с обновлением  
 Подробный список поддерживаемых версий и выпусков, которые можно обновить, см. в разделе [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
> [!TIP]  
>  Последние сведения о проблемах, связанных с SQL Server, см. в [заметах о выпуске SQL Server 2016](https://go.microsoft.com/fwlink/?LinkID=398124).  
  
  
##  <a name="side-by-side-installations"></a><a name="bkmk_side_by_side"></a> Параллельная установка  
 Службы SQL Server Reporting Services в собственном режиме можно установить параллельно с развертыванием служб [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] в собственном режиме.  
  
 Отсутствует поддержка параллельных развертываний служб SQL Server Reporting Services в режиме интеграции с SharePoint и всех предыдущих версий компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
  
##  <a name="in-place-upgrade"></a><a name="bkmk_inplace_upgrade"></a> Обновление на месте  
 Обновление завершается программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать для обновления любого компонента или всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Программа установки обнаружит существующие экземпляры и предложит выполнить обновление. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки позволяет использовать параметры обновления, которые можно указывать в качестве параметров командной строки или в мастере установки.  
  
 После запуска программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно либо обновить одну из следующих версий, либо установить новый экземпляр служб SQL Server Reporting Services, который будет выполняться параллельно с существующими установками.  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в следующих разделах:  

* [Обновление до SQL Server 2016](../../database-engine/install-windows/upgrade-sql-server.md)
* [Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)
* [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)
  
  
##  <a name="pre-upgrade-checklist"></a><a name="bkmk_upgrade_checklist"></a> Контрольный список действий перед обновлением  
 Перед обновлением до служб SQL Server Reporting Services проверьте следующие моменты.  
  
-   Ознакомьтесь с требованиями, чтобы определить, поддерживает ли оборудование и программное обеспечение службы [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]. Дополнительные сведения см. в разделе [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Используйте средство проверки конфигурации системы (SCC) для просмотра на компьютере сервера отчетов условий, которые могут препятствовать успешной установке служб SQL Server Reporting Services. Дополнительные сведения см. в разделе [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).  
  
-   Просмотрите рекомендации и руководство по безопасности для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
-   Создайте резервную копию симметричного ключа. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Создайте резервные копии баз данных сервера отчетов и файлов конфигурации. Дополнительные сведения см. в разделе [Backup and Restore Operations for Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md).  
  
-   Создайте резервные копии всех настроек виртуальных каталогов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , существующих в IIS.  
  
-   Удалите недопустимые TLS/SSL-сертификаты.  К ним относятся сертификаты с истекшим сроком действия, которые не планируется обновлять до обновления служб Reporting Services.  Наличие недопустимых сертификатов приведет к неудаче обновления, а в файл журнала служб Reporting Services будет записано сообщение об ошибке, аналогичное следующему: **Microsoft.ReportingServices.WmiProvider.WMIProviderException: A Secure Sockets Layer (SSL) certificate is not configured on the Web site.** (На веб-сайте не настроен SSL-сертификат).  
  
 Перед обновлением рабочей среды всегда запускайте проверку обновления в предварительной рабочей среде, имеющей аналогичную конфигурацию.  
  
  
## <a name="overview-of-migration-scenarios"></a>Общие сведения о сценариях миграции  
 При обновлении поддерживаемой версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в общем случае у вас будет возможность запустить мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обновить программные файлы, базу данных и все данные программы сервера отчетов.  
  
 Но при этом требуется **миграция** установки сервера отчетов вручную, если обнаруживаются любые из следующих условий.  
  
-   Вы хотите изменить тип сервера отчетов, используемого в вашем развертывании. Например, невозможно обновить или преобразовать сервер отчетов в собственном режиме в сервер, работающий в режиме интеграции с SharePoint. Дополнительные сведения см. в статье [Миграция из собственного режима в режим интеграции с SharePoint (службы SSRS)](../../reporting-services/install-windows/native-to-sharepoint-migration-ssrs.md).  
  
-   Нужно уменьшить время, на которое сервер отчетов переводится в режим «вне сети» во время процесса обновления. Текущая установка остается в режиме «в сети» при копировании данных содержимого на новый экземпляр сервера отчетов и проверки установки без изменения состояния существующей установки сервера отчетов.  
  
-   Требуется выполнить миграцию развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 2010 на SharePoint 2013/2016. SharePoint 2013/2016 не поддерживает обновление на месте из SharePoint 2010. Дополнительные сведения см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
  
##  <a name="native-mode-upgrade-and-migration-scenarios"></a><a name="bkmk_native_scenarios"></a> Обновление в собственном режиме и сценарии миграции  
 **Обновление.** Обновление на месте в собственном режиме выполняется одинаково для каждой из поддерживаемых версий, перечисленных ранее в этом разделе. Запустите мастер установки SQL Server или процесс установки из командной строки. После установки база данных сервера отчетов автоматически обновляется до новой схемы базы данных сервера отчетов. Дополнительные сведения см. в разделе [Обновление на месте](#bkmk_inplace_upgrade) этой статьи.  
  
 Процесс обновления начинается с выбора существующего экземпляра сервера отчетов, подлежащего обновлению.  
  
1.  Если база данных сервера отчетов размещается на удаленном компьютере и у вас нет разрешения на обновление этой базы данных, программа установки предложит вам представить учетные данные для обновления базы данных удаленного сервера отчетов. Обязательно представьте учетные данные, имеющие разрешение **sysadmin** или разрешение на обновление базы данных.  
  
2.  Программа установки выявляет обстоятельства или настройки, не позволяющие осуществлять обновление, и считывает параметры конфигурации. Ниже представлены примеры, включающие пользовательские модули, развернутые на сервере отчетов. Если обновление заблокировано, необходимо либо модифицировать установку так, чтобы этот процесс был разблокирован, либо перейти на новый экземпляр служб SQL Server Reporting Services. Дополнительные сведения см. в документации помощника по обновлению.  
  
3.  Если процесс обновления может быть продолжен, программа установки предлагает продолжить его выполнение.  
  
4.  Программа установки создает новые папки для программных файлов служб SQL Server Reporting Services. К числу программных папок для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] относится MSRS13.\<*instance name*>.  
  
5.  Программа установки добавляет программные файлы сервера отчетов служб SQL Server Reporting Services, средства настройки, а также программы командной строки, которые входят в состав компонента сервера отчетов.  
  
    1.  Программные файлы предшествующих версий удаляются.  
  
    2.  К средствам настройки сервера отчетов и программам, обновляемым до уровня новой версии, относятся средство настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме, утилиты командной строки, такие как RS.exe, а также построитель отчетов.  
  
    3.  Другие клиентские средства, такие как [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , скачиваются и обновляются отдельно. Дополнительные сведения см. в разделе [Скачивание SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
  
    4.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] загружается отдельно. Дополнительные сведения см. в разделе [SQL Server Data Tools в Visual Studio 2015](https://msdn.microsoft.com/mt186501).  
  
6.  Программа установки повторно использует запись службы в диспетчере управления службами для службы сервера отчетов служб SQL Server Reporting Services. Эта запись службы включает учетную запись службы Windows сервера отчетов.  
  
7.  Программа установки резервирует новые URL-адреса в соответствии с существующими настройками виртуального каталога в службах IIS. Программа установки может не удалить виртуальные каталоги в IIS, поэтому не забывайте удалять их вручную по завершении процесса обновления.  
  
8.  Программа установки осуществляет слияние параметров в файлах конфигурации. При использовании в качестве основы файлов конфигурации из текущей установки добавляются новые записи. Устаревшие записи не удаляются, но по завершении процесса обновления они не считываются сервером отчетов. Старые файлы регистрации, устаревший файл RSWebApplication.config и установки виртуального каталога в IIS при обновлении не удаляются. Более старые версии конструктора отчетов, среда Management Studio и другие клиентские средства при обновлении не удаляются. Если они больше не нужны, позаботьтесь об удалении этих файлов и средств по завершении обновления.  
  
 **Миграция.** Миграция предыдущей версии установки в собственном режиме в службы SQL Server Reporting Services выполняется одинаково для всех поддерживаемых версий, перечисленных ранее в этом разделе. Дополнительные сведения см. в статье [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
  
##  <a name="upgrade-a-reporting-services-native-mode-scale-out-deployment"></a><a name="bkmk_native_scaleout"></a> Обновление масштабного развертывания служб Reporting Services, работающих в собственном режиме  
 Ниже приводится сводка действий по обновлению развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме, которое масштабировано на использование более одного сервера отчетов. Этот процесс требует остановки развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
1.  Создайте резервные копии ключей шифрования и баз данных сервера отчетов. Дополнительные сведения см. в статьях [Операции резервного копирования и восстановления для служб Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md) и [Добавление и удаление ключей шифрования для развертывания с горизонтальным увеличением масштаба (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md).  
  
2.  Используйте диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и удалите все серверы отчетов из масштабированного развертывания. Дополнительные сведения см. в разделе [Настройка развертывания с горизонтальным увеличением масштаба для сервера отчетов в собственном режиме (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
3.  Обновите один из серверов отчетов до служб SQL Server Reporting Services.  
  
4.  Используйте диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для добавления серверов отчетов обратно в развертывание. Дополнительные сведения см. в разделе [Настройка развертывания с горизонтальным увеличением масштаба для сервера отчетов в собственном режиме (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
     Для каждого сервера повторите шаги по обновлению и масштабированию.  
  
##  <a name="sharepoint-mode-upgrade-and-migration-scenarios"></a><a name="bkmk_sharePoint_scenarios"></a> Обновление в режиме интеграции с SharePoint и сценарии миграции  
 В следующих разделах приводится описание возможных проблем и основных шагов, необходимых для обновления или миграции с определенных версий [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint на службы SQL Server Reporting Services [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint.  
  
 Есть два компонента установки для обновления развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared Service.  
  
    > [!TIP]  
    >  Используйте командлет [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint `Get-SPRSServiceApplicationServers` , чтобы определить серверы в ферме SharePoint, на которых в данный момент выполняется общая служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint и которые потому подлежат обновлению.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint. Дополнительные сведения см. в статье [Установка и удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Подробные инструкции по переносу установки в режиме SharePoint см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
> [!IMPORTANT]  
>  При выполнении некоторых из следующих сценариев для среды SharePoint неизбежно время простоя. Это вызвано необходимостью обновления различных технологий. Если простой неприемлем, необходимо вместо обновления на месте выполнить миграцию.  
  
### <a name="sssql14-to-sql-server-reporting-services"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] на службы SQL Server Reporting Services  
 **Начальная среда:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 1 (SP1), SharePoint 2010 или SharePoint 2013.  
  
 **Целевая среда.** Службы SQL Server Reporting Services, SharePoint 2013 или SharePoint 2016.   
  
-   **SharePoint 2013/2016.** SharePoint 2013/2016 не поддерживает обновление на месте из SharePoint 2010. Однако процедура **обновления присоединением базы данных поддерживается**  .
  
     Если имеется установленная версия [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированная с SharePoint 2010, нельзя обновить сервер SharePoint на месте. Однако можно выполнить миграцию баз данных содержимого и баз данных приложений службы из фермы SharePoint 2010 в ферму SharePoint 2013/2016.  
  
### <a name="sssql11-to-sql-server-reporting-services"></a>[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] на службы SQL Server Reporting Services  
 **Начальная среда:** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)], SharePoint 2010.  
  
 **Целевая среда.** Службы SQL Server Reporting Services, SharePoint 2013 или SharePoint 2016.   
  
-   **SharePoint 2013/2016.** SharePoint 2013/2016 не поддерживает обновление на месте из SharePoint 2010. Однако процедура **обновления присоединением базы данных поддерживается**  .
  
     Если имеется установленная версия [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированная с SharePoint 2010, нельзя обновить сервер SharePoint на месте. Однако можно выполнить миграцию баз данных содержимого и баз данных приложений службы из фермы SharePoint 2010 в ферму SharePoint 2013/2016.  
  
### <a name="sskilimanjaro-to-sql-server-reporting-services"></a>[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] на службы SQL Server Reporting Services  
 **Начальная среда:** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SharePoint 2010.  
  
 **Целевая среда.** Службы SQL Server Reporting Services, SharePoint 2013 или SharePoint 2016.  
 
-   **SharePoint 2013/2016.** SharePoint 2013/2016 не поддерживает обновление на месте из SharePoint 2010. Однако процедура **обновления присоединением базы данных поддерживается**  .

    Следует перенести SharePoint, прежде чем можно будет обновить службы Reporting Services.
  
-   Установите версию служб SQL Server Reporting Services надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint на все клиентские веб-интерфейсы в ферме. Установить надстройку можно с помощью мастера установки служб SQL Server Reporting Services или с помощью загрузки надстройки.  
  
-   Запустите установку служб SQL Server Reporting Services, чтобы обновить режим интеграции с SharePoint для всех "серверов отчетов". Мастер установки SQL Server устанавливает службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и создает новое приложение службы. 
  
  
##  <a name="considerations-for-a-migration"></a><a name="bkmk_migration_considerations"></a> Вопросы миграции  
 При перемещении данных приложения необходимо помнить о следующих проблемах и ограничениях.  
  
-   Для защиты ключа шифрования применяется хэш, содержащий идентификатор компьютера.  
  
-   Имена баз данных сервера отчетов фиксированы и не могут быть изменены на новом компьютере.  
  
### <a name="encryption-key-considerations"></a>Дополнительные сведения о ключе шифрования  
 Всегда создавайте резервные копии ключей шифрования перед перемещением базы данных сервера отчетов на новый компьютер.  
  
 При перемещении установки сервера отчетов на другой компьютер становится недействительным хэш, который защищает ключи шифрования, используемые для защиты конфиденциальных данных в базе данных сервера отчетов. Каждый экземпляр сервера отчетов, который использует базу данных, имеет собственную копию ключа шифрования, которая шифруется с удостоверением учетной записи службы, как она определена на текущем компьютере. Если сменить компьютеры, служба не будет иметь доступа к своему ключу, даже если использовать такое же имя учетной записи на новом компьютере.  
  
 Чтобы восстановить обратимое шифрование на новом компьютере сервера отчетов, необходимо восстановить ключ, резервная копия которого была сделана ранее. Полный набор ключей, хранимых в базе данных сервера отчетов, состоит из значения симметричного ключа и идентификатора службы, используемых для ограничения доступа к ключу, чтобы он мог использоваться только экземпляром сервера отчетов, на котором был сохранен. В процессе восстановления ключа сервер отчетов заменяет существующие копии ключа новыми версиями. Новая версия содержит значения идентификаторов компьютера и службы, как они определены на текущем компьютере. Дополнительные сведения см. в следующих разделах:  
  
-   Режим интеграции с SharePoint: см. раздел "Управление ключами" статьи [Управление служебным приложением SharePoint службы Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  
  
-   Собственный режим: см. статью [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
  
### <a name="fixed-database-name"></a>Фиксированное имя базы данных  
 Нельзя переименовать базу данных сервера отчетов. Идентификатор базы данных записывается в хранимых процедурах сервера отчетов при создании базы данных. Переименование первичной или временной баз данных сервера отчетов приведет к ошибкам при запуске процедур, что нарушит функционирование установки сервера отчетов.  
  
 Если имя базы данных из существующей установки непригодно для новой установки, то необходимо рассмотреть возможность создания новой базы данных с предпочтительным именем, а затем загрузить существующие данные приложения с использованием методов из следующего списка.  
  
-   Запишите [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] скрипт, который вызывает методы SOAP веб-службы сервера отчетов, чтобы копировать данные между базами данных. Можно использовать служебную программу RS.exe для выполнения скрипта. Дополнительные сведения об этом подходе см. в статье [Сценарии и PowerShell со службами Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md).  
  
-   Запишите код, который вызывает поставщика инструментария WMI, чтобы копировать данные между базами данных. Дополнительные сведения об этом подходе см. в статье [Доступ к поставщику WMI для служб Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  
  
-   Если количество элементов невелико, можно переиздать отчеты и общие источники данных из конструктора отчетов, конструктора моделей и построителя отчетов на новом сервере отчетов. Необходимо создать повторно назначения ролей, подписки, общие расписания, расписания моментальных снимков отчета, пользовательские свойства, установленные для отчетов или других элементов, безопасность элементов модели и свойства, назначенные на сервере отчетов. Будут потеряны журнал отчетов и данные журнала выполнения отчета.  
  
  
##  <a name="additional-resources"></a><a name="bkmk_additional_resources"></a> Дополнительные ресурсы  
  
> [!NOTE]  
>  Дополнительные сведения об обновлении присоединением базы данных SharePoint см. в разделах:  
  
-   [Общие сведения о процессе обновления до SharePoint 2016](https://technet.microsoft.com/library/cc262483\(v=office.16\)).

-   [Общие сведения о процессе обновления до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).
  
-   [Подготовка с очисткой перед обновлением до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Обновление баз данных с SharePoint 2013 до SharePoint 2016](https://technet.microsoft.com/library/cc303436\(v=office.16\)).

-   [Обновление баз данных с SharePoint 2010 до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).  

## <a name="next-steps"></a>Дальнейшие действия

[Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md)   
[Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
