---
title: Операции резервного копирования и восстановления для служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services], backing up
- databases [Reporting Services], restoring
- databases [Reporting Services], moving
- backing up databases [Reporting Services]
- moving databases
- restoring databases [Reporting Services]
- files [Reporting Services], restoring
- files [Reporting Services], backing up
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: aa16c9f5520bd135e7ea2fc3ef13809c04eb05c2
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030145"
---
# <a name="backup-and-restore-operations-for-reporting-services"></a>Операции резервного копирования и восстановления для служб Reporting Services
  В этом разделе представлены общие сведения обо всех файлах данных, использованных при установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а также содержится описание времени и способа создания резервных копий этих файлов. Разработка плана создания резервных копий и восстановления баз данных сервера отчетов является самой важной частью в стратегии восстановления. Однако более полная стратегия восстановления включает дополнительные компоненты, в том числе создание резервных копий ключей шифрования, пользовательских сборок или модулей, файлов конфигурации и исходных файлов для отчетов и моделей.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint  
  
 Операции создания резервных копий и восстановления часто используются для перемещения всей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или ее части.  
  
-   Переместить на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только базы данных сервера отчета можно с помощью создания резервной копии и восстановления, либо операций присоединения и отсоединения. Дополнительные сведения см. в разделе [перемещение баз данных сервера отчетов на другой компьютер &#40;собственный режим служб SSRS&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
-   Перемещение экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на новый компьютер называется миграцией. При миграции экземпляра запускается программа установки, чтобы установить новый образец сервера отчетов и затем скопировать данные экземпляра на новый компьютер. Дополнительные сведение о миграции установки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в следующих разделах:  
  
    -   [Обновление и перенос служб Reporting Services](upgrade-and-migrate-reporting-services.md)  
  
    -   [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [Перенос установки служб Reporting Services (собственный режим)](migrate-a-reporting-services-installation-native-mode.md)  
  
## <a name="backing-up-the-report-server-databases"></a>Создание резервных копий баз данных сервера отчетов  
 Так как сервер отчетов является сервером без сохранения состояния, все данные приложений хранятся в базах данных **reportserver** и **reportservertempdb** , которые выполняются на экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Можно создать резервные копии баз данных **reportserver** и **reportservertempdb** с помощью одного из поддерживаемых методов создания резервных копий баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для баз данных сервера отчетов рекомендуется следующее:  
  
-   Используйте полную модель восстановления для создания резервной копии базы данных **reportserver** .  
  
-   Используйте простую модель восстановления для создания резервной копии базы данных **reportservertempdb** .  
  
-   Можно использовать разные расписания для резервного копирования каждой базы данных. Единственная причина создания резервной копии базы данных **reportservertempdb** состоит в том, чтобы избежать необходимости ее повторного создания в случае сбоя оборудования. В случае сбоя оборудования нет необходимости восстанавливать данные в базе данных **reportservertempdb**, однако необходима структура таблицы. При утере базы данных **reportservertempdb**единственный способ вернуть ее — это повторно создать базу данных сервера отчетов. При повторном создании базы данных **reportservertempdb**очень важно, чтобы она имела тоже имя, что и первичная база данных сервера отчетов.  
  
 Дополнительные сведения о резервном копировании и восстановлении реляционных баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
> [!IMPORTANT]  
>  Если сервер отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] находится в режиме интеграции с SharePoint, следует учитывать дополнительные базы данных, включая базы данных конфигурации SharePoint и базы данных предупреждений [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . В режиме интеграции с SharePoint для каждого приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] создаются три базы данных. Базы данных **reportserver**, **reportservertempdb**и **dataalerting** . Дополнительные сведения см. в разделе [Backup and Restore Reporting Services SharePoint Service Applications](../backup-and-restore-reporting-services-sharepoint-service-applications.md)(Резервное копирование и восстановление приложений службы Reporting Services SharePoint).  
  
## <a name="backing-up-the-encryption-keys"></a>Создание резервных копий ключей шифрования  
 При первой настройке установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] необходимо создать резервную копию ключей шифрования. Кроме того, необходимо создавать резервные копии ключей шифрования каждый раз при изменении удостоверения учетных записей служб или изменении имени компьютера. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md). Сведения о серверах отчетов в режиме интеграции с SharePoint см. в разделе "Управление ключами" статьи [Управление приложением службы SharePoint — Reporting Services](../manage-a-reporting-services-sharepoint-service-application.md).  
  
## <a name="backing-up-the-configuration-files"></a>Создание резервной копии файлов конфигурации  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используются файлы конфигурации. Необходимо создать резервную копию этих файлов при первой настройке сервера, а также после развертывания каких-либо пользовательских модулей. Необходимо создать резервные копии следующих файлов:  
  
-   Rsreportserver.config  
  
-   Rssvrpolicy.config  
  
-   Rsmgrpolicy.config;  
  
-   Reportingservicesservice.exe.config;  
  
-   Web.config — для приложений [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] сервера отчетов и диспетчера отчетов;  
  
-   Machine.config для [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]  
  
## <a name="backing-up-data-files"></a>Резервное копирование файлов данных  
 Создайте резервные копии файлов, которые создаются и обслуживаются в конструкторе отчетов и конструкторе моделей. Они включают файлы определения отчета (RDL), файлы моделей отчета (SMDL), файлы общих источников данных (RDS), файлы представлений данных (DV), файлы источников данных (DS), файлы проекта сервера отчетов (RPTPROJ), а также файлы решения отчетов (SLN).  
  
 Не забывайте о создании резервных копий любых файлов скрипта (.rss), которые создаются для задач администрирования или развертывания.  
  
 Убедитесь в наличии резервной копии любых используемых пользовательских модулей и пользовательских сборок.  
  
## <a name="see-also"></a>См. также  
 [База данных сервера отчетов (службы Reporting Services в собственном режиме)](../report-server/report-server-database-ssrs-native-mode.md)   
 [Файлы конфигурации служб Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Программа rskeymgmt (SSRS)](../tools/rskeymgmt-utility-ssrs.md)   
 [Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Администрирование базы данных сервера отчетов (службы SSRS в собственном режиме)](../report-server/administer-a-report-server-database-ssrs-native-mode.md)   
 [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
