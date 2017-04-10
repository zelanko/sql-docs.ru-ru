---
title: "Установка SQL Server&#160;2016 | Microsoft Docs"
ms.custom: ""
ms.date: "04/13/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.portal.Installation.f1"
helpviewer_keywords: 
  - "установка SQL Server, начальная установка"
  - "установка [SQL Server]"
  - "первоначальная установка [SQL Server]"
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Установка SQL Server&#160;2016
  Мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет единое дерево компонентов для установки всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Компоненты соединения  
  
 Начиная с SQL Server 2016 средства управления SQL Server больше не устанавливаются из дерева основных компонентов. Дополнительные сведения см. в статье [Установка средств управления SQL Server со средой SSMS](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md).  
  
 Каждый компонент можно установить отдельно или выбрать сочетания перечисленных выше компонентов. Чтобы выбрать среди имеющихся выпусков и компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] те, которые лучше всего вам подходят, см. разделы [Выпуски и компоненты SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) и [Возможности, поддерживаемые различными выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## В этом разделе  
 Независимо от способа установки служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с помощью мастера установки или командной строки) программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнят следующие три шага:  
  
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
 Описывает подготовку компьютера к установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Требования к оборудованию и программному обеспечению.  
  
-   Требования средства проверки конфигурации и критические препятствия.  
  
-   Соображения безопасности.  
  
 [Установка SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)  
 Описывает параметры установки для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Справочник по пользовательскому интерфейсу программы установки SQL Server](../Topic/SQL%20Server%20Setup%20User%20Interface%20Reference.md)  
 Описывает режимы установки, доступные в мастере установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Обновление до SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
 Описывает параметры обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Удаление SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)  
 Описывает процедуры установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается процедура установки и настройки кластера отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Установка компонентов бизнес-аналитики SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компоненты, которые являются частью платформы бизнес-аналитики Майкрософт, включают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и несколько клиентских приложений, используемых для создания аналитических данных или работы с ними. В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается, как установить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## Дополнительные сведения  
 [Установка компонентов бизнес-аналитики SQL Server с SharePoint (Power Pivot и службы Reporting Services)](../Topic/Install%20SQL%20Server%20BI%20Features%20with%20SharePoint%20\(Power%20Pivot%20and%20Reporting%20Services\).md)  
 В этом разделе описывается установка компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде SharePoint. В нем указано, какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить при использовании той или иной версии и выпуска SharePoint. В нем также описаны процедуры установки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint и служб Reporting Services в режиме интеграции с SharePoint.  
  
 ![ssrs_fyi_note](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) Установите новый образец базы данных [Wide World Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx). 
  
 [Дополнительные образцы кода и баз данных SQL Server](http://sqlserversamples.codeplex.com/)  
 Описывает установку и настройку образцов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также образцов баз данных.  
  
Ссылки и сведения для всех поддерживаемых версий [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] см. в [Центре обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx).  
  
## См. также:  
 [Новые возможности установки SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
  
  