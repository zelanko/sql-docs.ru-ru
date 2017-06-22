---
title: "Обновление и перенос служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSRS, upgrading
- Reporting Services, upgrades
- SQL Server Reporting Services, upgrading
- upgrading Reporting Services
ms.assetid: 851a19a8-07ab-4d42-992f-1986c4c8df55
caps.latest.revision: 92
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e7144b243b14ea3f65d912552ce8e6cdd736ab59
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---

# <a name="upgrade-and-migrate-reporting-services"></a>Обновление и перенос служб Reporting Services

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  В этом разделе приведен обзор параметров обновления и миграции для служб SQL Server Reporting Services. Существует два принципиальных подхода к обновлению развертывания служб SQL Server Reporting Services.  
  
-   **Обновление.** Обновляются компоненты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на тех серверах и экземплярах, где они установлены в данный момент. Обычно это называется обновлением на месте. Обновление на месте с одного режима сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на другой режим не поддерживается. Например, невозможно обновить сервер отчетов в собственном режиме до сервера отчетов в режиме интеграции с SharePoint. Элементы отчета можно переносить из одного режима в другой. Дополнительные сведения см. в разделе «Миграция из собственного режима в режим интеграции с SharePoint» далее в этом документе.  
  
-   **Миграция**. Устанавливается и настраивается новая среда SharePoint, в нее копируются элементы отчетов и ресурсы, а затем выполняется настройка новой среды для использования существующего содержимого. Более низкая форма миграции — копирование баз данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], файлов конфигурации и при использовании режима интеграции с SharePoint баз данных содержимого SharePoint.  
    
> **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Основной режим &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции
  
##  <a name="bkmk_known_issues"></a> Известные проблемы и рекомендации, связанные с обновлением  
 Подробный список поддерживаемых версий и выпусков, которые можно обновить, см. в разделе [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
> [!TIP]  
>  Последние сведения о проблемах с SQL Server см. в следующих:  
>   
>  -   [Заметки о выпуске SQL Server 2016](http://go.microsoft.com/fwlink/?LinkID=398124).  
  
  
##  <a name="bkmk_side_by_side"></a> Параллельная установка  
 SQL Server Reporting Services собственный режим может быть установленных side-by-side с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] развертывание собственного режима.  
  
 Поддержка развертываний side-by-side служб SQL Server Reporting Services в режиме интеграции с SharePoint и все предыдущие версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] компоненты режиме интеграции с SharePoint.  
  
  
##  <a name="bkmk_inplace_upgrade"></a> Обновление на месте  
 Обновление завершается программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать для обновления любого компонента или всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Программа установки обнаружит существующие экземпляры и предложит выполнить обновление. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки позволяет использовать параметры обновления, которые можно указывать в качестве параметров командной строки или в мастере установки.  
  
 При запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программы установки, можно выбрать параметр, чтобы обновить одну из следующих версий, или можно установить новый экземпляр SQL Server Reporting Services, работающей side-by-side существующие установки:  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в следующих разделах:  

* [Обновление до SQL Server 2016](../../database-engine/install-windows/upgrade-sql-server.md)
* [Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)
* [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)
  
  
##  <a name="bkmk_upgrade_checklist"></a> Контрольный список действий перед обновлением  
 Перед обновлением до SQL Server Reporting Services, проверьте следующее.  
  
-   Ознакомьтесь с требованиями, чтобы определить, поддерживает ли оборудование и программное обеспечение службы [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]. Дополнительные сведения см. в разделе [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Средство проверки конфигурации системы (SCC) используется для просмотра на компьютере сервера отчетов условий, которые могут препятствовать успешной установке служб SQL Server Reporting Services. Дополнительные сведения см. в разделе [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).  
  
-   Просмотрите рекомендации и руководство по безопасности для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
-   Создайте резервную копию симметричного ключа. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Создайте резервные копии баз данных сервера отчетов и файлов конфигурации. Дополнительные сведения см. в разделе [Backup and Restore Operations for Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md).  
  
-   Создайте резервные копии всех настроек виртуальных каталогов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , существующих в IIS.  
  
-   Удалите недопустимые SSL-сертификаты.  К ним относятся сертификаты с истекшим сроком действия, которые не планируется обновлять до обновления служб Reporting Services.  Наличие недопустимых сертификатов приведет к неудаче обновления, а в файл журнала служб Reporting Services будет записано сообщение об ошибке, аналогичное следующему: **Microsoft.ReportingServices.WmiProvider.WMIProviderException: A Secure Sockets Layer (SSL) certificate is not configured on the Web site**.  
  
 Перед обновлением рабочей среды всегда запускайте проверку обновления в предварительной рабочей среде, имеющей аналогичную конфигурацию.  
  
  
## <a name="overview-of-migration-scenarios"></a>Общие сведения о сценариях миграции  
 При обновлении поддерживаемой версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в общем случае у вас будет возможность запустить мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обновить программные файлы, базу данных и все данные программы сервера отчетов.  
  
 Но при этом требуется **миграция** установки сервера отчетов вручную, если обнаруживаются любые из следующих условий.  
  
-   Вы хотите изменить тип сервера отчетов, используемого в вашем развертывании. Например, невозможно обновить или преобразовать сервер отчетов в собственном режиме в сервер, работающий в режиме интеграции с SharePoint. Дополнительные сведения см. в статье [Миграция из собственного режима в режим интеграции с SharePoint (SSRS)](../../reporting-services/install-windows/native-to-sharepoint-migration-ssrs.md).  
  
-   Нужно уменьшить время, на которое сервер отчетов переводится в режим «вне сети» во время процесса обновления. Текущая установка остается в режиме «в сети» при копировании данных содержимого на новый экземпляр сервера отчетов и проверки установки без изменения состояния существующей установки сервера отчетов.  
  
-   Требуется выполнить миграцию развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 2010 на SharePoint 2013/2016. SharePoint 2013/2016 не поддерживает обновление на месте из SharePoint 2010. Дополнительные сведения см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
  
##  <a name="bkmk_native_scenarios"></a> Обновление в собственном режиме и сценарии миграции  
 **Обновление** . Обновление на месте в собственном режиме представляет собой один процесс для всех поддерживаемых версий, перечисленных ранее в этом разделе. Запустите мастер установки SQL Server или процесс установки из командной строки. После установки база данных сервера отчетов автоматически обновляется до новой схемы базы данных сервера отчетов. Дополнительные сведения см. в разделе [Обновление на месте](#bkmk_inplace_upgrade) этой статьи.  
  
 Процесс обновления начинается с выбора существующего экземпляра сервера отчетов, подлежащего обновлению.  
  
1.  Если база данных сервера отчетов размещается на удаленном компьютере и у вас нет разрешения на обновление этой базы данных, программа установки предложит вам представить учетные данные для обновления базы данных удаленного сервера отчетов. Обязательно представьте учетные данные, имеющие разрешение **sysadmin** или разрешение на обновление базы данных.  
  
2.  Программа установки выявляет обстоятельства или настройки, не позволяющие осуществлять обновление, и считывает параметры конфигурации. Ниже представлены примеры, включающие пользовательские модули, развернутые на сервере отчетов. Если обновление заблокировано, необходимо либо изменить установку, чтобы обновление больше не блокируются, либо выполнить миграцию в новый экземпляр SQL Server Reporting Services. Дополнительные сведения см. в документации помощника по обновлению.  
  
3.  Если процесс обновления может быть продолжен, программа установки предлагает продолжить его выполнение.  
  
4.  Программа установки создает новые папки для файлов программы SQL Server Reporting Services. Программных папок для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установка включает MSRS13.\< *имя экземпляра*>.  
  
5.  Программа установки добавляет программные файлы сервера отчетов SQL Server Reporting Services, средства настройки и служебные программы командной строки, которые входят в состав компонента сервера отчетов.  
  
    1.  Программные файлы предшествующих версий удаляются.  
  
    2.  К средствам настройки сервера отчетов и программам, обновляемым до уровня новой версии, относятся средство настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме, утилиты командной строки, такие как RS.exe, а также построитель отчетов.  
  
    3.  Другие клиентские средства, такие как [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , скачиваются и обновляются отдельно. Дополнительные сведения см. в разделе [Скачивание SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
  
    4.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] загружается отдельно. Дополнительные сведения см. в разделе [SQL Server Data Tools в Visual Studio 2015](https://msdn.microsoft.com/mt186501).  
  
6.  Программа установки повторно использует запись службы в диспетчере управления службами для службы сервера отчетов служб отчетов SQL Server. Эта запись службы включает учетную запись службы Windows сервера отчетов.  
  
7.  Программа установки резервирует новые URL-адреса в соответствии с существующими настройками виртуального каталога в службах IIS. Программа установки может не удалить виртуальные каталоги в IIS, поэтому не забывайте удалять их вручную по завершении процесса обновления.  
  
8.  Программа установки осуществляет слияние параметров в файлах конфигурации. При использовании в качестве основы файлов конфигурации из текущей установки добавляются новые записи. Устаревшие записи не удаляются, но по завершении процесса обновления они не считываются сервером отчетов. Старые файлы регистрации, устаревший файл RSWebApplication.config и установки виртуального каталога в IIS при обновлении не удаляются. Более старые версии конструктора отчетов, среда Management Studio и другие клиентские средства при обновлении не удаляются. Если они больше не нужны, позаботьтесь об удалении этих файлов и средств по завершении обновления.  
  
 **Миграция:** миграция предыдущей версии установки в собственном режиме в SQL Server Reporting Services имеет те же действия для всех поддерживаемых версий, перечисленных ранее в этом разделе. Дополнительные сведения см. в статье [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
  
##  <a name="bkmk_native_scaleout"></a> Обновление масштабного развертывания служб Reporting Services, работающих в собственном режиме  
 Ниже приводится сводка действий по обновлению развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме, которое масштабировано на использование более одного сервера отчетов. Этот процесс требует остановки развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
1.  Создайте резервные копии ключей шифрования и баз данных сервера отчетов. Дополнительные сведения см. в статьях [Операции резервного копирования и восстановления для служб Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md) и [Добавление и удаление ключей шифрования для масштабного развертывания (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md).  
  
2.  Используйте диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и удалите все серверы отчетов из масштабированного развертывания. Дополнительные сведения см. в разделе [Настройка масштабного развертывания сервера отчетов в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
3.  Обновите один из серверов отчетов служб SQL Server Reporting Services.  
  
4.  Используйте диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для добавления серверов отчетов обратно в развертывание. Дополнительные сведения см. в статье [Настройка масштабного развертывания сервера отчетов в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
     Для каждого сервера повторите шаги по обновлению и масштабированию.  
  
##  <a name="bkmk_sharePoint_scenarios"></a> Обновление в режиме интеграции с SharePoint и сценарии миграции  
 В следующих разделах описаны проблемы и основных шагов, необходимых для обновления или миграции с определенных версий [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint служб SQL Server Reporting Services [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint.  
  
 Есть два компонента установки для обновления развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared Service.  
  
    > [!TIP]  
    >  Используйте командлет [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint `Get-SPRSServiceApplicationServers` , чтобы определить серверы в ферме SharePoint, на которых в данный момент выполняется общая служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint и которые потому подлежат обновлению.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint. Дополнительные сведения см. в статье [Установка и удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Подробные инструкции по переносу установки в режиме SharePoint см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
> [!IMPORTANT]  
>  При выполнении некоторых из следующих сценариев для среды SharePoint неизбежно время простоя. Это вызвано необходимостью обновления различных технологий. Если простой неприемлем, необходимо вместо обновления на месте выполнить миграцию.  
  
### <a name="includesssql14includessssql14-mdmd-to-sql-server-reporting-services"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]в SQL Server Reporting Services  
 **Начальная среда:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 1 (SP1), SharePoint 2010 или SharePoint 2013.  
  
 **Конечная среда:** служб отчетов SQL Server, SharePoint 2013 или SharePoint 2016.   
  
-   **SharePoint 2013/2016:** не поддерживается обновление SharePoint 2010 на месте до SharePoint 2013/2016. Однако процедура **обновления присоединением базы данных поддерживается**  .
  
     Если имеется установленная версия [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированная с SharePoint 2010, нельзя обновить сервер SharePoint на месте. Однако можно выполнить миграцию баз данных содержимого и баз данных приложений службы из фермы SharePoint 2010 в ферму SharePoint 2013/2016.  
  
### <a name="includesssql11includessssql11-mdmd-to-sql-server-reporting-services"></a>[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]в SQL Server Reporting Services  
 **Начальная среда:** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)], SharePoint 2010.  
  
 **Конечная среда:** служб отчетов SQL Server, SharePoint 2013 или SharePoint 2016.   
  
-   **SharePoint 2013/2016:** не поддерживается обновление SharePoint 2010 на месте до SharePoint 2013/2016. Однако процедура **обновления присоединением базы данных поддерживается**  .
  
     Если имеется установленная версия [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированная с SharePoint 2010, нельзя обновить сервер SharePoint на месте. Однако можно выполнить миграцию баз данных содержимого и баз данных приложений службы из фермы SharePoint 2010 в ферму SharePoint 2013/2016.  
  
### <a name="includesskilimanjaroincludessskilimanjaro-mdmd-to-sql-server-reporting-services"></a>[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]в SQL Server Reporting Services  
 **Starting environment:** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SharePoint 2010.  
  
 **Конечная среда:** служб отчетов SQL Server, SharePoint 2013 или SharePoint 2016.  
 
-   **SharePoint 2013/2016:** не поддерживается обновление SharePoint 2010 на месте до SharePoint 2013/2016. Однако процедура **обновления присоединением базы данных поддерживается**  .

    Следует перенести SharePoint, прежде чем можно будет обновить службы Reporting Services.
  
-   Установите версию SQL Server Reporting Services [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройка для SharePoint на каждом веб-интерфейса в ферме. Надстройку можно установить с помощью мастера установки SQL Server Reporting Services или с помощью загрузки надстройки.  
  
-   Запустите установку SQL Server Reporting Services для обновления в режиме SharePoint для каждого «серверов отчетов». Мастер установки SQL Server устанавливает службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и создает новое приложение службы. 
  
  
##  <a name="bkmk_migration_considerations"></a> Вопросы миграции  
 При перемещении данных приложения необходимо помнить о следующих проблемах и ограничениях.  
  
-   Для защиты ключа шифрования применяется хэш, содержащий идентификатор компьютера.  
  
-   Имена баз данных сервера отчетов фиксированы и не могут быть изменены на новом компьютере.  
  
### <a name="encryption-key-considerations"></a>Дополнительные сведения о ключе шифрования  
 Всегда создавайте резервные копии ключей шифрования перед перемещением базы данных сервера отчетов на новый компьютер.  
  
 При перемещении установки сервера отчетов на другой компьютер становится недействительным хэш, который защищает ключи шифрования, используемые для защиты конфиденциальных данных в базе данных сервера отчетов. Каждый экземпляр сервера отчетов, который использует базу данных, имеет собственную копию ключа шифрования, которая шифруется с удостоверением учетной записи службы, как она определена на текущем компьютере. Если сменить компьютеры, служба не будет иметь доступа к своему ключу, даже если использовать такое же имя учетной записи на новом компьютере.  
  
 Чтобы восстановить обратимое шифрование на новом компьютере сервера отчетов, необходимо восстановить ключ, резервная копия которого была сделана ранее. Полный набор ключей, хранимых в базе данных сервера отчетов, состоит из значения симметричного ключа и идентификатора службы, используемых для ограничения доступа к ключу, чтобы он мог использоваться только экземпляром сервера отчетов, на котором был сохранен. В процессе восстановления ключа сервер отчетов заменяет существующие копии ключа новыми версиями. Новая версия содержит значения идентификаторов компьютера и службы, как они определены на текущем компьютере. Дополнительные сведения см. в следующих разделах:  
  
-   Режим SharePoint: см. раздел "Управление ключами" статьи [Управление служебным приложением SharePoint службы Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  
  
-   Собственный режим: см. статью [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
### <a name="fixed-database-name"></a>Фиксированное имя базы данных  
 Нельзя переименовать базу данных сервера отчетов. Идентификатор базы данных записывается в хранимых процедурах сервера отчетов при создании базы данных. Переименование первичной или временной баз данных сервера отчетов приведет к ошибкам при запуске процедур, что нарушит функционирование установки сервера отчетов.  
  
 Если имя базы данных из существующей установки непригодно для новой установки, то необходимо рассмотреть возможность создания новой базы данных с предпочтительным именем, а затем загрузить существующие данные приложения с использованием методов из следующего списка.  
  
-   Запишите [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] скрипт, который вызывает методы SOAP веб-службы сервера отчетов, чтобы копировать данные между базами данных. Можно использовать служебную программу RS.exe для выполнения скрипта. Дополнительные сведения об этом подходе см. в статье [Сценарии и PowerShell со службами Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md).  
  
-   Запишите код, который вызывает поставщика инструментария WMI, чтобы копировать данные между базами данных. Дополнительные сведения об этом подходе см. в статье [Доступ к поставщику WMI для служб Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  
  
-   Если число элементов невелико, можно переиздать отчеты, модели отчетов и общие источники данных из конструктора отчетов, конструктора моделей и построителя отчетов на новом сервере отчетов. Необходимо создать повторно назначения ролей, подписки, общие расписания, расписания моментальных снимков отчета, пользовательские свойства, установленные для отчетов или других элементов, безопасность элементов модели и свойства, назначенные на сервере отчетов. Будут потеряны журнал отчетов и данные журнала выполнения отчета.  
  
  
##  <a name="bkmk_additional_resources"></a> Дополнительные ресурсы  
  
> [!NOTE]  
>  Дополнительные сведения об обновлении присоединением базы данных SharePoint см. в разделах:  
  
-   [Общие сведения о процессе обновления до SharePoint 2016](https://technet.microsoft.com/library/cc262483\(v=office.16\)).

-   [Общие сведения о процессе обновления до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688).
  
-   [Подготовка с очисткой перед обновлением до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Обновление баз данных с SharePoint 2013 до SharePoint 2016](https://technet.microsoft.com/library/cc303436\(v=office.16\)).

-   [Обновление баз данных с SharePoint 2010 до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690).  

## <a name="next-steps"></a>Следующие шаги

[Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md)   
[Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
