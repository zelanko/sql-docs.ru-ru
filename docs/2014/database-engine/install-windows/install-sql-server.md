---
title: Установка SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5ed522c64e0f9652e3ffb310f98348c402193ef8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68889243"
---
# <a name="install-sql-server-2014"></a>Установка SQL Server 2014
## <a name="download-sql-server-2014-express"></a>[Загрузка SQL Server 2014 Express](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Благодарим вас на [Скотт Hanselman](http://www.hanselman.com/) по сбору всех ссылок на пакеты установщика в одном месте!**
  
 В этом разделе представлены общие сведения о разных параметрах установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения о различных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонентах, которые можно установить, а также о процессе установки, см. в разделе [Установка SQL Server 2014](installation-for-sql-server.md).  
> **Примечание.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступно в 32-разрядных и 64-разрядных выпусках. Установка 64-разрядной и 32-разрядной версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может производиться либо с помощью мастера установки, либо из командной строки. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонентах см. в разделе [выпуски и компоненты SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) и [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 По умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы баз данных и образцы кода не устанавливаются. Чтобы установить образцы баз данных и образцы кода для выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме выпуска Express, посетите [веб-сайт CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843). Сведения о поддержке образцов баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и образцы кода для [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]см. в разделе [Обзор баз данных и образцов](https://go.microsoft.com/fwlink/?LinkId=110391).  
  
 Ознакомьтесь с требованиями по установке, сведениями о проверках конфигурации системы и вопросами безопасности перед тем, как устанавливать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md). В подразделах следующего раздела приведены сведения о различных вариантах установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
  
## <a name="install-sscurrent-components"></a>Установка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] компонентов  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[О компоненте SQL Server Database Engine](../sql-server-database-engine-overview.md)|Описывает установку и настройку компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Установка репликации SQL Server](install-sql-server-replication.md)|Описывает установку и настройку репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Установка распределенного воспроизведения](../../tools/distributed-replay/install-distributed-replay-overview.md)|Содержит список разделов, связанных с установкой компонента распределенного воспроизведения.|  
|[Установка базовой версии средств управления SQL Server](../../sql-server/install/install-sql-server-management-tools.md)|Описывает, как установить и настроить средства управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Установка компонентов SQL Server PowerShell](install-sql-server-powershell.md)|Описывает соображения относительно установки компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.|  
  
## <a name="how-to-install-sscurrent"></a>Как установить[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Инструкции по установке](../../sql-server/install/installation-how-to-topics.md)|В этом разделе приведены ссылки на методические разделы по установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью мастера установки, из командной строки, с помощью файлов конфигурации и с помощью программы SysPrep.|  
|[Установка SQL Server 2014 в операционной системе Server Core](install-sql-server-on-server-core.md)|В этом разделе описана установка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на Windows Server Core.|  
|[Проверка установки SQL Server](validate-a-sql-server-installation.md)|Описано использование отчета обнаружения SQL для проверки того, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере.|  
|[Параметры для средства проверки конфигурации системы](check-parameters-for-the-system-configuration-checker.md)|Содержит обсуждение функций средства проверки конфигурации (SCC).|  
  
## <a name="configuration"></a>Конфигурация  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|В этом разделе приведены общие сведения о конфигурации брандмауэра и описан процесс настройки брандмауэра Windows.|  
|[Настройка многосетевого компьютера для доступа к SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|В этом разделе описываются настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и брандмауэра Windows в режиме повышенной безопасности для предоставления сетевого подключения экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в многосетевой среде.|  
|[Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|Выполнив действия, описанные в этом разделе, можно настроить порт и брандмауэр, разрешив доступ к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или PowerPivot для SharePoint.|  
  
## <a name="related-sections"></a>Связанные разделы  
 [Install SQL Server 2014 BI Features](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 Функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые являются частью платформы бизнес-аналитики [!INCLUDE[msCoName](../../includes/msconame-md.md)], включающей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] и несколько клиентских приложений, используемых для создания аналитических данных или работы с ними. В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассказывается, как установить [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается процедура установки и настройки кластера отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Обновление до SQL Server 2014](upgrade-sql-server.md)   
 [Удаление SQL Server 2014](../../sql-server/install/uninstall-sql-server.md)   
 [Решения высокого уровня доступности (SQL Server)](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  
