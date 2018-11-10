---
title: Установка SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48bfd8ddc0a7e68bc2747543f5e079f24041c20a
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018169"
---
# <a name="installation-for-sql-server-2014"></a>Установка SQL Server 2014
 ## <a name="-download-sql-server-2014-express-httpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[ Скачивание SQL Server 2014 Express ](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Выражаем благодарность [(Scott hanselman)](http://www.hanselman.com/) для сбора всех ссылок пакета установщика в одном месте.**
  
  Мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет единое дерево компонентов для установки всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Средства управления  
  
-   Компоненты соединения  
  
 Каждый компонент можно установить отдельно или выбрать сочетания перечисленных выше компонентов. Чтобы сделать доступным в наиболее подходящий выпуск и компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [выпуски и компоненты SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) и [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Доступны 32-разрядный и 64-разрядный выпуски [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
 
 **Попробуйте продукт:**  
  
-   Есть учетная запись Azure?  Затем перейдите **[здесь](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** запустить виртуальную машину с SQL Server 2014 с пакетом обновления 1 (SP1) уже установлен. Дополнительные сведения о SQL Server 2014 (SP1), см. в разделе [сведения о выпуске пакета обновления 1 для SQL Server 2014 ](https://support.microsoft.com/en-us/kb/3058865).  
  
## <a name="in-this-section"></a>в этом разделе  
 Независимо от способа установки служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с помощью мастера установки или командной строки) программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполнят следующие три шага:  
  
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
 Описывает подготовку компьютера к установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Требования к оборудованию и программному обеспечению.  
  
-   Требования средства проверки конфигурации и критические препятствия.  
  
-   Соображения безопасности.  
  
 [Установка SQL Server 2014](install-sql-server.md)  
 Описывает параметры установки для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Обновление до SQL Server 2014](upgrade-sql-server.md)  
 Описывает параметры обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Удаление SQL Server 2014](../../sql-server/install/uninstall-sql-server.md)  
 Описывает процедуры установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается процедура установки и настройки кластера отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 [Установка компонентов бизнес-Аналитики SQL Server 2014](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компоненты, которые являются частью платформы бизнес-аналитики Майкрософт, включают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и несколько клиентских приложений, используемых для создания аналитических данных или работы с ними. В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается, как установить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="related-sections"></a>См. также  
 [Инструкции по установке](../../sql-server/install/installation-how-to-topics.md)  
 В этом разделе приведены ссылки на методические разделы по установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью мастера установки, из командной строки, с помощью файлов конфигурации и с помощью программы SysPrep.  
  
 [Установка компонентов бизнес-Аналитики SQL Server с SharePoint &#40;PowerPivot и служб Reporting Services&#41;](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 В этом разделе описывается установка компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде SharePoint. В нем указано, какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить при использовании той или иной версии и выпуска SharePoint. В нем также описаны процедуры установки PowerPivot для SharePoint и служб Reporting Services в режиме SharePoint.  
  
 [Установка образцов SQL Server и образцов баз данных](http://sqlserversamples.codeplex.com/)  
 Описывает установку и настройку образцов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также образцов баз данных.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности установки SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
