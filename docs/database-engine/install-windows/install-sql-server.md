---
title: "Установка SQL Server | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/24/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- AdventureWorks sample database
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 59
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f07eec3427ee1e691da665323455bb35690dc93a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server"></a>Установка SQL Server

 > Материалы по предыдущим версиям SQL Server см. в статье [Установка SQL Server 2014](https://msdn.microsoft.com/en-US/library/bb500395(SQL.120).aspx).

 Начиная с [!INCLUDE[sssql15](../../includes/sssql15-md.md)], [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] доступен только в виде 64-разрядного приложения. Ниже приведены важные подробности о том, как получить и установить SQL Server.

## <a name="installation-details"></a>Подробности об установке
  
*  **Варианты**. Установка может производиться через мастер установки, из командной строки или с помощью SysPrep.
 
*  **Требования**. Перед установкой ознакомьтесь с требованиями к установке, проверками конфигурации системы и рекомендациями по безопасности в статье [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md) 

* **Процесс**. Полные инструкции по процедуре установки см. в статье [Установка SQL Server](../../database-engine/install-windows/installation-for-sql-server-2016.md) .

* **Образцы баз данных и примеры кода**: 
    * Они не устанавливаются по умолчанию в ходе установки SQL Server. 
    * Чтобы установить их для отличных от Express выпусков SQL Server, перейдите на веб-сайт [GitHub](http://github.com/Microsoft/sql-server-samples).
    

## <a name="get-the-installation-media"></a>Получение установочного носителя

Место, откуда можно скачать [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)], зависит от выпуска.

- **Выпуски Enterprise, Standard и Express SQL Server** предназначены для использования в рабочей среде. Чтобы получить установочный носитель с выпуском Enterprise или Standard, обратитесь к своему поставщику программного обеспечения. Сведения о приобретении и каталог партнеров Майкрософт можно найти на [веб-сайте приобретения продуктов Майкрософт](https://www.microsoft.com/en-us/server-cloud/products/sql-server/overview.aspx). 

- **Бесплатные выпуски** доступны на [странице загружаемых файлов SQL Server](http://www.microsoft.com/sql-server/sql-server-downloads).

## <a name="how-to-install-includessnoversionincludesssnoversion-mdmd"></a>Как установить [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]
 
|Title|Description|  
|-----------|-----------------|  
|[ Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] в Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md)|В этом разделе описана установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] на Windows Server Core.|  
|[Параметры для средства проверки конфигурации системы](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Содержит обсуждение функций средства проверки конфигурации (SCC).|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] с помощью мастера установки (программа установки)](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)|Методический раздел, описывающий типичную установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи мастера установки.|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Методический раздел, в котором приведены образцы синтаксиса и параметров для запуска установки в автоматическом режиме.|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] с помощью файла конфигурации](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Методический раздел, в котором приведены образцы синтаксиса и параметров для запуска установки с помощью файла конфигурации.|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] с помощью ](../../database-engine/install-windows/install-sql-server-using-sysprep.md)|Методическая статья, в которой приведены примеры синтаксиса и параметров для запуска установки с помощью SysPrep.|  
|[Добавление компонентов в экземпляр [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] (программа установки)](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Методический раздел, описывающий обновление компонентов существующего экземпляра [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Исправление неудавшейся установки [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)|Методический раздел, описывающий исправление поврежденной установки [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Переименование компьютера, на который установлен изолированный экземпляр SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Методический раздел, описывающий обновление системных метаданных, хранящихся в таблице sys.servers.|  
|[Установка обновлений для обслуживания [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/install-sql-server-servicing-updates.md)|Методическая статья об установке обновлений для [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|Методический раздел, описывающий проверку ошибок в файлах журнала установки.|  
|[Проверка установки SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Описано использование отчета обнаружения SQL для проверки того, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере.|  
  
  
## <a name="how-to-install-individual-components"></a>Установка отдельных компонентов  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Установка ядра СУБД SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Описывает установку и настройку компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Установка репликации SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Описывает установку и настройку репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Установка распределенного воспроизведения — обзор](../../tools/distributed-replay/install-distributed-replay-overview.md)|Содержит список разделов, связанных с установкой компонента распределенного воспроизведения.|  
|[Установка средств управления SQL Server со средой SSMS](http://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)|Описывает, как установить и настроить средства управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Установка компонентов SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Описывает соображения относительно установки компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.|  
  

## <a name="how-to-configure-sql-server"></a>Настройка SQL Server  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|В этом разделе приведены общие сведения о конфигурации брандмауэра и описан процесс настройки брандмауэра Windows.|  
|[Настройка многосетевого компьютера для доступа к SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|В этом разделе описываются настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и брандмауэра Windows в режиме повышенной безопасности для предоставления сетевого подключения экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в многосетевой среде.|  
|[Настройка брандмауэра Windows для разрешения доступа к службам Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Выполнив действия, описанные в этом разделе, можно настроить порт и брандмауэр, разрешив доступ к [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint.|  
  
## <a name="related-sections"></a>См. также  
[Возможности, поддерживаемые различными выпусками [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)  
[Установка функций бизнес-аналитики [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
  [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>См. также:  

[Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Обновление до [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/upgrade-sql-server.md)   
 [Удаление [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/uninstall-sql-server.md)   
 [Решения высокого уровня доступности &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  

