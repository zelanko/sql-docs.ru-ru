---
title: Установка SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: quickstart
helpviewer_keywords:
- AdventureWorks sample database
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: b4f60e7041801d67f93dab467b574e5d0da54e7d
ms.sourcegitcommit: 27c267bf2a3cfaf2abcb5f3777534803bf4cffe5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73240747"
---
# <a name="install-sql-server"></a>Установка SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье приводятся рекомендации по установке SQL Server в Windows.

Дополнительные сведения о других сценариях развертывания см. в следующих источниках:

- [Linux](../../linux/sql-server-linux-setup.md)
- [Контейнеры Docker](../../linux/sql-server-linux-configure-docker.md)
- [Kubernetes — кластеры больших данных](../../big-data-cluster/deploy-get-started.md)

Начиная с [!INCLUDE[sssql15](../../includes/sssql15-md.md)], [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] доступен только в виде 64-разрядного приложения. Ниже приведены важные подробности о том, как получить и установить SQL Server.

## <a name="installation-details"></a>Подробности об установке
  
*  **Варианты**. Установка может производиться через мастер установки, из командной строки или с помощью SysPrep.
 
*  **Требования**. Перед установкой ознакомьтесь с требованиями к установке, проверками конфигурации системы и рекомендациями по безопасности в статье [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md). 

* **Процесс**. Полные инструкции по процедуре установки см. в статье [Установка SQL Server](../../database-engine/install-windows/installation-for-sql-server-2016.md).

* **Образцы баз данных и примеры кода**: 
    * Они не устанавливаются по умолчанию в ходе установки SQL Server. 
    * Чтобы установить их для отличных от Express выпусков SQL Server, перейдите на веб-сайт [GitHub](https://github.com/Microsoft/sql-server-samples).
    

## <a name="get-the-installation-media"></a>Получение установочного носителя

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="how-to-install-includessnoversionincludesssnoversion-mdmd"></a>Как установить [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]
 
|Title|Описание|  
|-----------|-----------------|  
|[ Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] в Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md)|В этой статье описана установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] в Windows Server Core.|  
|[Параметры для средства проверки конфигурации системы](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Содержит обсуждение функций средства проверки конфигурации (SCC).|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] с помощью мастера установки (программа установки)](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)|Методическая статья с описанием типичной установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью мастера установки.|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Методическая статья, в которой приведены образцы синтаксиса и параметров для запуска установки в автоматическом режиме.|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] с помощью файла конфигурации](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Методическая статья, в которой приведены образцы синтаксиса и параметров для запуска установки с помощью файла конфигурации.|  
|[Установка [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] с помощью ](../../database-engine/install-windows/install-sql-server-using-sysprep.md)|Методическая статья, в которой приведены примеры синтаксиса и параметров для запуска установки с помощью SysPrep.|  
|[Добавление компонентов в экземпляр [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] (программа установки)](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Методическая статья с описанием обновления компонентов существующего экземпляра [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Исправление неудавшейся установки [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)|Методическая статья с описанием исправления поврежденной установки [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Переименование компьютера, на который установлен изолированный экземпляр SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Методическая статья, в которой описывается обновление системных метаданных, хранящихся в таблице sys.servers.|  
|[Установка обновлений для обслуживания [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/install-sql-server-servicing-updates.md)|Методическая статья об установке обновлений для [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|Методическая статья, в которой описывается проверка ошибок в файлах журнала установки.|  
|[Проверка установки SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Описано использование отчета обнаружения SQL для проверки того, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере.|  
  
  
## <a name="how-to-install-individual-components"></a>Установка отдельных компонентов  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Установка ядра СУБД SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Описывает установку и настройку компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Установка репликации SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Описывает установку и настройку репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Установка распределенного воспроизведения — обзор](../../tools/distributed-replay/install-distributed-replay-overview.md)|Содержит список статей, связанных с установкой компонента распределенного воспроизведения.|  
|[Установка средств управления SQL Server со средой SSMS](https://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)|Описывает, как установить и настроить средства управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Установка компонентов SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Описывает соображения относительно установки компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.|  
  

## <a name="how-to-configure-sql-server"></a>Настройка SQL Server  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|В этой статье приведены общие сведения о конфигурации брандмауэра и описан процесс настройки брандмауэра Windows.|  
|[Настройка многосетевого компьютера для доступа к SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|В этой статье описываются настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и брандмауэра Windows в режиме повышенной безопасности для предоставления сетевого подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в многосетевой среде.|  
|[Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|Выполнив действия, описанные в этой статье, можно настроить порт и брандмауэр, чтобы разрешить доступ к [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint.|  
  
## <a name="related-sections"></a>См. также  
[Возможности, поддерживаемые различными выпусками [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)  
[Установка функций бизнес-аналитики [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
  [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>См. также раздел  

[Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Обновление до [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/upgrade-sql-server.md)   
 [Удаление [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/uninstall-sql-server.md)   
 [Решения высокого уровня доступности &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  
