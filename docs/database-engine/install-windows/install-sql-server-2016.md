---
title: "Установка SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "образец базы данных AdventureWorks"
  - "установка SQL Server, подготовка к установке"
  - "установка [SQL Server]"
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 59
ms.author: "mikeray"
manager: "jhubbard"
---
# Установка SQL Server 2016
  SQL Server 2016 — это 64-разрядное приложение. Ниже приведены важные подробности о том, как получить и установить SQL Server.

## <a name="installation-details"></a>Подробности об установке
  
*  **Варианты**. Установка может производиться через мастер установки, из командной строки или с помощью SysPrep.
 
*  **Требования**. Перед установкой ознакомьтесь с требованиями к установке, проверками конфигурации системы и рекомендациями по безопасности в статье [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md). 

* **Процесс**. Полные инструкции по процедуре установки см. в статье [Установка SQL Server](../../database-engine/install-windows/installation-for-sql-server-2016.md).

* **Образцы баз данных и примеры кода**: 
    * Они не устанавливаются по умолчанию в ходе установки SQL Server. 
    * Чтобы установить их для отличных от Express выпусков SQL Server, перейдите на [веб-сайт CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843).
    * Информацию о поддержке по образцам баз данных SQL Server и примерам кода для SQL Server Express см. в статье [Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391) (Обзор баз данных и примеров кода).
    

## <a name="get-the-installation-media"></a>Получение установочного носителя

Место, откуда можно скачать [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], зависит от выпуска.

- **Выпуски Enterprise, Standard и Express SQL Server** предназначены для использования в рабочей среде. Чтобы получить установочный носитель с выпуском Enterprise или Standard, обратитесь к своему поставщику программного обеспечения. Сведения о приобретении и каталог партнеров Майкрософт можно найти на [веб-сайте приобретения продуктов Майкрософт](https://www.microsoft.com/en-us/server-cloud/products/sql-server/overview.aspx). 

- **Бесплатные выпуски** доступны по следующим ссылкам:

| Выпуск | Description
|---------|--------
|[Developer Edition](http://myprodscussu1.app.vssubscriptions.visualstudio.com/Downloads?q=SQL%20Server%20Developer) | Бесплатный полнофункциональный набор ПО SQL Server 2016 Enterprise Edition, который позволяет разработчикам создавать, тестировать и демонстрировать приложения в нерабочей среде. 
|[Express Edition](http://www.microsoft.com/download/details.aspx?id=52679)|  Бесплатное решение начального уровня, которое идеально подходит для развертывания небольших баз данных в рабочих средах. Позволяет создавать классические и небольшие серверные приложения, управляемые данными, которые занимают на диске до 10 ГБ. 
| [Evaluation Edition](http://technet.microsoft.com/evalcenter/mt130694) | Полнофункциональный набор ПО SQL Server Enterprise Edition для ознакомительного использования в течение 180 дней.
   
 
  

## <a name="how-to-install-sql-server"></a>Установка SQL Server
 
|Title|Description|  
|-----------|-----------------|  
|[Установка SQL Server 2016 на Server Core](../../database-engine/install-windows/install-sql-server-2016-on-server-core.md)|В этом разделе описана установка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на Windows Server Core.|  
|[Параметры для средства проверки конфигурации системы](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Содержит обсуждение функций средства проверки конфигурации (SCC).|  
|[Установка SQL Server 2016 с помощью мастера установки &#40;программа установки&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)|Методический раздел, описывающий типичную установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи мастера установки.|  
|[Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Методический раздел, в котором приведены образцы синтаксиса и параметров для запуска установки в автоматическом режиме.|  
|[Установка SQL Server 2016, с помощью файла конфигурации](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Методический раздел, в котором приведены образцы синтаксиса и параметров для запуска установки с помощью файла конфигурации.|  
|[Установка SQL Server 2016 с помощью SysPrep](../../database-engine/install-windows/install-sql-server-2016-using-sysprep.md)|Методическая статья, в которой приведены примеры синтаксиса и параметров для запуска установки с помощью SysPrep.|  
|[Добавление компонентов в экземпляр SQL Server 2016 &#40;программа установки&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Методический раздел, описывающий обновление компонентов существующего экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Исправление неудавшейся установки SQL Server 2016](../../database-engine/install-windows/repair-a-failed-sql-server-2016-installation.md)|Методический раздел, описывающий исправление поврежденной установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Переименование компьютера, на который установлен изолированный экземпляр SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Методический раздел, описывающий обновление системных метаданных, хранящихся в таблице sys.servers.|  
|[Установка обновлений для обслуживания SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016-servicing-updates.md)|Методическая статья об установке обновлений для SQL Server 2016.|  
|[Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|Методический раздел, описывающий проверку ошибок в файлах журнала установки.|  
|[Проверка установки SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Описано использование отчета обнаружения SQL для проверки того, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере.|  
  
  
## <a name="how-to-install-individual-components"></a>Установка отдельных компонентов  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Установка ядра СУБД SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Описывает установку и настройку компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Установка репликации SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Описывает установку и настройку репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Установка распределенного воспроизведения — обзор](../../tools/distributed-replay/install-distributed-replay-overview.md)|Содержит список разделов, связанных с установкой компонента распределенного воспроизведения.|  
|[Установка средств управления SQL Server со средой SSMS](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md)|Описывает, как установить и настроить средства управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Установка компонентов SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Описывает соображения относительно установки компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.|  
  

## <a name="how-to-configure-sql-server"></a>Настройка SQL Server  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|В этом разделе приведены общие сведения о конфигурации брандмауэра и описан процесс настройки брандмауэра Windows.|  
|[Настройка многосетевого компьютера для доступа к SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|В этом разделе описываются настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и брандмауэра Windows в режиме повышенной безопасности для предоставления сетевого подключения экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в многосетевой среде.|  
|[Настройка брандмауэра Windows для разрешения доступа к службам Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Выполнив действия, описанные в этом разделе, можно настроить порт и брандмауэр, разрешив доступ к [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint.|  
  
## <a name="related-sections"></a>См. также  
[Возможности, поддерживаемые различными выпусками SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
[Установка компонентов бизнес-аналитики SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
  [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>См. также:  

[Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Обновление до SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)   
 [Удаление SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)   
 [Решения высокого уровня доступности &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  