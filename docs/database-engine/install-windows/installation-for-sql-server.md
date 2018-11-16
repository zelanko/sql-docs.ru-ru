---
title: Установка SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 09/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql13.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: e85f782e8229d6f1515ba9265cfe3e7c8910318a
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603592"
---
# <a name="sql-server-installation"></a>Установка SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет единое дерево компонентов для установки всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
-   Компоненты соединения  
  
Начиная с [!INCLUDE[ss2016](../../includes/sssql15-md.md)], средства управления SQL Server больше не устанавливаются из дерева основных компонентов. Дополнительные сведения см. в статье [Скачивание SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).  
  
Каждый компонент можно установить отдельно или выбрать сочетания перечисленных выше компонентов. Чтобы выбрать среди имеющихся выпусков и компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] те, которые лучше всего вам подходят, см. разделы о функциях, поддерживаемых вашей версией SQL Server:

- [Выпуски и поддерживаемые функции [!INCLUDE[ss2017](../../includes/sssqlv14-md.md)]](~/sql-server/editions-and-components-of-sql-server-2017.md).  
- [Выпуски и поддерживаемые функции [!INCLUDE[ss2016](../../includes/sssql15-md.md)]](~/sql-server/editions-and-components-of-sql-server-2016.md).  
- [Возможности, поддерживаемые различными выпусками [!INCLUDE[ss2014](../../includes/sssql14-md.md)]](https://technet.microsoft.com/library/cc645993(v=sql.120).aspx)
  
## <a name="in-this-section"></a>в этом разделе  
Независимо от способа установки служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с помощью мастера установки или командной строки) программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполнят следующие три шага:  
  
[Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
Описывает подготовку компьютера к установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Требования к оборудованию и программному обеспечению.  
-   Требования средства проверки конфигурации и критические препятствия.  
-   Соображения безопасности.  
  
[Установка SQL Server](../../database-engine/install-windows/install-sql-server.md)  
 Описывает параметры установки для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
[Справочник по пользовательскому интерфейсу программы установки SQL Server](https://msdn.microsoft.com/library/183b5cdd-962e-41ca-8064-ea44f622c77d)  
 Описывает режимы установки, доступные в мастере установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
[Обновление SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)  
 Описывает параметры обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
[Удаление SQL Server](../../sql-server/install/uninstall-sql-server.md)  
 Описывает процедуры установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
[Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается процедура установки и настройки кластера отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
[Установка компонентов бизнес-аналитики SQL Server](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компоненты, которые являются частью платформы бизнес-аналитики Майкрософт, включают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и несколько клиентских приложений, используемых для создания аналитических данных или работы с ними. В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описывается, как установить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="more-information"></a>Дополнительные сведения
[Установка компонентов бизнес-аналитики SQL Server с SharePoint (Power Pivot и службы Reporting Services)](https://msdn.microsoft.com/library/3166107c-30c2-468e-bb1b-bb42b79b37c3)  
 В этом разделе описывается установка компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде SharePoint. В нем указано, какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить при использовании той или иной версии и выпуска SharePoint. В нем также описаны процедуры установки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint и служб Reporting Services в режиме интеграции с SharePoint.  
  
![ssrs_fyi_note](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) Установите новый образец базы данных [Wide World Importers](../../sample/world-wide-importers/wide-world-importers-documentation.md). 
  
[Дополнительные образцы кода и баз данных SQL Server](https://sqlserversamples.codeplex.com/)  
 Описывает установку и настройку образцов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также образцов баз данных.  
  
Ссылки и сведения для всех поддерживаемых версий [см. в](https://msdn.microsoft.com/library/ff803383.aspx) Центре обновления SQL Server [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
[Новые возможности установки SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
[Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
