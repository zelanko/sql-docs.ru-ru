---
title: Быстрая установка SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- quick start installation [SQL Server]
- installation [SQL Server]
- installing SQL Server, quick start installations
ms.assetid: 672afac9-364d-4946-ad5d-8a2d89cf8d81
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b06f5248152f8a11bf3e46d222df457f5442b6b4
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60157250"
---
# <a name="quick-start-installation-of-sql-server-2014"></a>Быстрая установка SQL Server 2014
    
## <a name="introduction"></a>Введение  
 Мастер установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] построен на основе установщика Windows. Он предоставляет единое дерево функций для установки следующих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]  
  
-   Средства управления  
  
-   Компоненты соединения  
  
 Каждый компонент можно установить отдельно или выбрать сочетания перечисленных выше компонентов. Чтобы сделать доступным в наиболее подходящий выпуск и компоненты [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], см. в разделе [выпуски и компоненты SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).  
  
 Доступны 32-разрядный и 64-разрядный выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Программа установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает следующие параметры установки.  
  
-   **Мастер установки**  
  
     См. в разделе [Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41; ](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) методические сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью мастера установки.  
  
-   **Командная строка**  
  
     См. в разделе [Установка SQL Server 2014 из командной строки](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) образцы синтаксиса и параметров для запуска автоматической установки.  
  
-   **Файл конфигурации**  
  
     См. в разделе [Установка SQL Server 2014 с помощью файла конфигурации](../database-engine/install-windows/install-sql-server-using-a-configuration-file.md) образцы синтаксиса и параметров для запуска установки с помощью файла конфигурации.  
  
-   **SysPrep**  
  
     См. в разделе [Установка SQL Server 2014 с помощью SysPrep](../database-engine/install-windows/install-sql-server-using-sysprep.md) методические сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью средства SysPrep.  
  
-   **Установка основных серверных компонентов**  
  
     См. в разделе [Установка SQL Server 2014 на Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md) методические сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Windows Server Core.  
  
-   **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Установка компонентов бизнес-Аналитики**  
  
     См. в разделе [Установка компонентов SQL Server 2014 BI](../sql-server/install/install-sql-server-business-intelligence-features.md) сведения об установке компонентов, которые являются частью платформы бизнес-Аналитики Майкрософт, которые включают [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]и несколько клиентские приложения, используемых для создания и работы с аналитическими данными.  
  
-   **Установка отказоустойчивого кластера**  
  
     См. в разделе [Установка отказоустойчивого кластера SQL Server](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) методические сведения об установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отказоустойчивого кластера.  
  
 По умолчанию при установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] образцы баз данных и образцы кода не устанавливаются. Чтобы установить образцы баз данных и образцы кода для выпусков [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], кроме выпуска Express, посетите [веб-сайт CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843). Сведения о поддержке образцов баз данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и образцы кода для [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]см. в разделе [Обзор баз данных и образцов](https://go.microsoft.com/fwlink/?LinkId=110391).  
  
## <a name="includessnoversionincludesssnoversion-mdmd-installation"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Установка  
 Независимо от того, используется для установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] мастер установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или командная строка, процесс установки включает один или несколько шагов.  
  
-   Ознакомьтесь с требованиями по установке, сведениями о проверках конфигурации системы и вопросами безопасности для установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  Дополнительные сведения см. в статье [Planning a SQL Server Installation](quick-start-installation-of-sql-server-2014.md#BKMK_BeforeYouInstall).  
  
-   Запустите программу установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для обновления существующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] до версии [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [обновление до SQL Server 2014](#BKMK_Upgrading).  
  
-   Запустите программу установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для установки нового экземпляра [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [установки SQL Server 2014](#BKMK_Install).  
  
-   После завершения установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] следующим действием будет настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и компонентов. Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] при помощи программ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Настройка SQL Server 2014](#BKMK_Configure).  
  
 В следующем разделе содержатся подробные пояснения к этим задачам.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
###  <a name="BKMK_BeforeYouInstall"></a> Планирование [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] установки  
 Перед установкой служб [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] следует ознакомиться с требованиями к оборудованию и программному обеспечению, рекомендациями относительно сети, Интернет и безопасности установки и запуска [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Планирование установки SQL Server](../../2014/sql-server/install/planning-a-sql-server-installation.md) и также в следующих разделах:  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Ознакомьтесь с требованиями к оборудованию и программному обеспечению, операционной системе, рекомендациями относительно сети, Интернета и требованиями относительно свободного места на жестком диске.|[Компоненты, необходимые для установки](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|Ознакомьтесь с вопросами безопасности для установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Вопросы безопасности](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)|  
|Ознакомьтесь со сведения о функциях, поддерживаемых разными выпусками [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Функции и выпуски](features-supported-by-the-editions-of-sql-server-2014.md)|  
|Выберите наиболее подходящий выпуск и компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Выпуски и компоненты SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md)|  
|Просмотрите конфигурацию оборудования и изучите процесс установки кластера отработки отказа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Подготовка к установке отказоустойчивого кластера](../sql-server/failover-clusters/install/before-installing-failover-clustering.md)|  
  
###  <a name="BKMK_Upgrading"></a> Обновление до [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Существующие экземпляры [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] можно обновить до [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [обновление до SQL Server 2014](../database-engine/install-windows/upgrade-sql-server.md). Перед запуском программы установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для обновления [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ознакомьтесь со следующими разделами, посвященными процессу обновления:  
  
|Описание|Раздел|  
|-----------------|-----------|  
|Документы поддерживают пути обновления до [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Поддерживаемые обновления](../database-engine/install-windows/supported-version-and-edition-upgrades.md)|  
|Описывает советник по переходу, средство, которое анализирует экземпляры [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] и [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] для выявления проблем с обновлением.|[Использование помощника по обновлению для подготовки к обновлениям](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)|  
|Описывает программу распределенного воспроизведения, которое позволяет использовать несколько компьютеров для воспроизведения данных трассировки, моделируя ответственную рабочую нагрузку. С помощью воспроизведения на тестовом сервере до и после обновления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно измерить разницу в производительности и обнаружить любые несовместимости приложения с обновлением.|[Использование программы распределенного воспроизведения для подготовки обновлений](../../2014/sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)|  
|Содержит список важных изменений, которые могут повлиять на работу приложений после обновления до [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Обратная совместимость](backward-compatibility.md)|  
|Методологический раздел по обновлению изолированного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Обновление до SQL Server 2014 с помощью мастера установки &#40;установки&#41;](../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|  
|Методологический раздел, посвященный обновленному выпуску [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] до следующего выпуска. Сведения о поддерживаемых способах обновления выпуска см. в разделе [Поддерживаемые обновления выпусков и версий](../database-engine/install-windows/supported-version-and-edition-upgrades.md).|[Обновление до другого выпуска SQL Server 2014 &#40;установки&#41;](../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает обновление [!INCLUDE[ssDE](../includes/ssde-md.md)] и [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] до отказоустойчивого кластера [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] отдельно на всех узлах отказоустойчивого кластера. Дополнительные сведения см. в этом разделе.|[Обновление отказоустойчивого кластера SQL Server](../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)|  
  
###  <a name="BKMK_Install"></a> Установка [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 В следующих разделах приведены сведения о различных вариантах установки [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
|Описание|Раздел|  
|-----------------|-----------|  
|Предоставляет ссылки на разделы, посвященные установке разных компонентов [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], и методические разделы, посвященные установке [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Установка SQL Server 2014](../database-engine/install-windows/install-sql-server.md)|  
|В этом разделе описана установка [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] на Windows Server Core.|[Установка SQL Server 2014 в Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md)|  
|Для добавления других функций к существующему экземпляру [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ознакомьтесь с данным разделом.|[Добавление компонентов к экземпляру SQL Server 2014 &#40;установки&#41;](../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md)|  
|Ознакомьтесь с этим разделом для создания нового экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Создание отказоустойчивого кластера SQL Server (программа установки)](../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|В этом разделе описано управление узлами в существующем экземпляре отказоустойчивого кластера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Добавление или удаление узлов отказоустойчивого кластера SQL Server (программа установки)](../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
|В этом разделе описана установка клиентских средств [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в отказоустойчивый кластер.|[Установка клиентских средств на отказоустойчивый кластер SQL Server](../sql-server/failover-clusters/install/install-client-tools-on-a-sql-server-failover-cluster.md)|  
|Описано использование отчета обнаружения SQL для проверки того, какая версия [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] установлены на компьютере.|[Проверка установки SQL Server](../database-engine/install-windows/validate-a-sql-server-installation.md)|  
|В этом разделе приведены ссылки на методические разделы по установке [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] с помощью мастера установки, из командной строки, с помощью файлов конфигурации и с помощью программы SysPrep.|[Инструкции по установке](../../2014/sql-server/install/installation-how-to-topics.md)|  
  
## <a name="related-content"></a>См. также  
 В этом разделе содержатся сведения о настройке и удалении [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
###  <a name="BKMK_Configure"></a> Настройка [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 После завершения установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно продолжить настройку [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью графических программ или программ командной строки. В следующих разделах содержатся сведения по первичной настройке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
|Описание|Раздел|  
|-----------------|-----------|  
|Приведенные в этом разделе сведения помогут определить, требуется ли разблокировать порты брандмауэра для доступа к службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или PowerPivot для SharePoint. Выполнив шаги, приведенные в этом разделе, можно настроить как параметры порта, так и брандмауэра.|[Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|  
|В разделе содержатся общие сведения о настройке брандмауэра и сводные сведения, представляющие интерес для администратора [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|В этом разделе описываются настройки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и брандмауэра Windows в режиме повышенной безопасности для предоставления сетевого подключения экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в многосетевой среде.|[Настройка многосетевого компьютера для доступа к SQL Server](../../2014/sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|  
  
###  <a name="BKMK_Uninstalling"></a> При удалении [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 В следующих разделах содержатся сведения о том, как вручную удалить изолированный экземпляр и экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|Описание|Раздел|  
|-----------------|-----------|  
|В данном разделе описан процесс удаления изолированного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]вручную.|[Удаление SQL Server 2014](../sql-server/install/uninstall-sql-server.md)|  
|В этом разделе рассматривается процесс удаления экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки)](../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)|  
|В этом разделе приводятся сведения об удалении объектов служб [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) вручную после удаления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или сервера служб DQS.|[Удаление объектов сервера служб Data Quality](../../2014/sql-server/install/remove-data-quality-server-objects.md)|  
  
## <a name="see-also"></a>См. также  
 [Спецификации SQL Server 2014](sql-server-2014-product-specifications.md)   
 [Начало работы с документацией по SQL Server](../2014-toc/books-online-for-sql-server-2014.md) [обратной совместимости](backward-compatibility.md)  
  
  
