---
description: Операции резервного копирования и восстановления для служб Reporting Services
title: Операции резервного копирования и восстановления для служб Reporting Services | Документы Майкрософт
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
ms.date: 05/08/2019
ms.openlocfilehash: dc0463e49bf19c60cab94a12c10c4d8e8289e848
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97402830"
---
# <a name="backup-and-restore-operations-for-reporting-services"></a>Операции резервного копирования и восстановления для служб Reporting Services

  В этой статье представлены общие сведения обо всех файлах данных, использовавшихся при установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], а также описание времени и порядка резервного копирования этих файлов. Разработка плана создания резервных копий и восстановления баз данных сервера отчетов является самой важной частью в стратегии восстановления. При этом более полная стратегия восстановления включает в себя создание резервных копий ключей шифрования, пользовательских сборок или модулей, файлов конфигурации и исходных файлов для отчетов.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.
  
 Операции создания резервных копий и восстановления часто используются для перемещения всей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или ее части.  
  
-   Переместить на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только базы данных сервера отчета можно с помощью создания резервной копии и восстановления, либо операций присоединения и отсоединения. Дополнительные сведения см. в разделе [Перемещение баз данных сервера отчетов на другой компьютер (собственный режим служб SSRS)](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
-   Перемещение экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на новый компьютер называется миграцией. При миграции экземпляра запускается программа установки, чтобы установить новый образец сервера отчетов и затем скопировать данные экземпляра на новый компьютер. Дополнительные сведения о переносе установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в следующих статьях.  
  
    - [Обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
    - [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  

    ::: moniker range="=sql-server-2016"
  
    - [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)  

    ::: moniker-end
  
## <a name="backing-up-the-report-server-databases"></a>Создание резервных копий баз данных сервера отчетов  
 Так как сервер отчетов является сервером без сохранения состояния, все данные приложений хранятся в базах данных **reportserver** и **reportservertempdb** , которые выполняются на экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Можно создать резервные копии баз данных **reportserver** и **reportservertempdb** с помощью одного из поддерживаемых методов создания резервных копий баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ниже приведены некоторые рекомендации, касающиеся баз данных сервера отчетов.  
  
-   Используйте полную модель восстановления для создания резервной копии базы данных **reportserver**.  
  
-   Используйте простую модель восстановления для создания резервной копии базы данных **reportservertempdb**.  
  
-   Можно использовать разные расписания для резервного копирования каждой базы данных. Единственная причина создания резервной копии базы данных **reportservertempdb** состоит в том, чтобы избежать ее повторного создания в случае сбоя оборудования. В случае сбоя оборудования нет необходимости восстанавливать данные в базе данных **reportservertempdb**, однако необходима структура таблицы. При утере базы данных **reportservertempdb** единственный способ вернуть ее — это повторно создать базу данных сервера отчетов. При повторном создании базы данных **reportservertempdb** очень важно, чтобы она имела тоже имя, что и первичная база данных сервера отчетов.  
  
 Дополнительные сведения о резервном копировании и восстановлении реляционных баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  

::: moniker range="=sql-server-2016"

> [!IMPORTANT]  
>  Если сервер отчетов находится в режиме интеграции с SharePoint, следует учитывать дополнительные базы данных, включая базы данных конфигурации SharePoint и базы данных предупреждений [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В режиме интеграции с SharePoint для каждого приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] создаются три базы данных. Базы данных **reportserver**, **reportservertempdb** и **dataalerting** . Дополнительные сведения см. в статье [Резервное копирование и восстановление приложений служб Reporting Services для SharePoint](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md).  

::: moniker-end
  
## <a name="backing-up-the-encryption-keys"></a>Создание резервных копий ключей шифрования  
 При первой настройке установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] необходимо создать резервную копию ключей шифрования. Кроме того, резервные копии ключей шифрования необходимо создавать при каждом изменении удостоверения учетных записей служб или изменении имени компьютера. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md). 

::: moniker range="=sql-server-2016"

Сведения о серверах отчетов в режиме интеграции с SharePoint см. в разделе "Управление ключами" статьи [Управление приложением службы SharePoint — Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  

::: moniker-end
  
## <a name="backing-up-the-configuration-files"></a>Создание резервной копии файлов конфигурации  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используются файлы конфигурации. Резервную копию этих файлов необходимо создать при первой настройке сервера, а также после развертывания каких-либо пользовательских модулей. Необходимо создать резервные копии следующих файлов:  
  
-   RSReportServer.config  
  
-   Rssvrpolicy.config  
  
-   Rsmgrpolicy.config;  
  
-   Reportingservicesservice.exe.config;  
  
-   Web.config для приложения [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] сервера отчетов
  
-   Machine.config для [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]  
  
## <a name="backing-up-data-files"></a>Резервное копирование файлов данных  
 Создайте резервные копии файлов, которые создаются и обслуживаются в конструкторе отчетов. В их число входят файлы определения отчета (RDL), файлы общих источников данных (RDS), файлы представлений данных (DV), файлы источников данных (DS), файлы проекта сервера отчетов (RPTPROJ), а также файлы решения отчетов (SLN).  
  
 Не забывайте создавать резервные копии всех файлов сценариев (RSS), которые создаются для задач администрирования или развертывания.  
  
 Убедитесь в наличии резервной копии любых используемых пользовательских модулей и пользовательских сборок.  

## <a name="next-steps"></a>Дальнейшие шаги

[База данных сервера отчетов](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
[Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
[Служебная программа rskeymgmt](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)   
[Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
[Администрирование базы данных сервера отчетов](../../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)   
[Настройка ключей шифрования и управление ими](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
