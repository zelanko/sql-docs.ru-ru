---
title: Руководство по использованию компонентов бизнес-Аналитики SQL Server в ферме SharePoint 2010 | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5f9a94c4-854b-4577-a8b1-7142f19904e3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ae552c12c3d4773d6a05a6d61c7644eb245b68ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094998"
---
# <a name="guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm"></a>Указания по использованию функций бизнес-аналитики SQL Server в ферме SharePoint 2010
  В этом разделе содержатся сведения о доступности компонентов в зависимости от версии и выпуска используемого ПО. Здесь также описываются требования по установке SharePoint 2010 для использования определенных компонентов SQL Server. Сведения, относящиеся к SharePoint 2013, см. в разделе [топологии развертывания для компонентов бизнес-Аналитики SQL Server в SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
 В этом разделе:  
  
-   [Общие требования SharePoint 2010](#bkmk_generalsharepoint)  
  
-   [SharePoint 2010 с пакетом обновления 1 (SP1)](#bkmk_sp1)  
  
-   [Поддержка выпусков SharePoint и компонентов бизнес-Аналитики](#bkmk_vers)  
  
-   [Средство подготовки продуктов SharePoint 2010](#bkmk_prereq)  
  
-   [Требования и рекомендации по установке SharePoint](#bkmk_install)  
  
##  <a name="bkmk_generalsharepoint"></a> Общие требования SharePoint 2010  
  
-   Продукты SharePoint 2010 имеют только 64-разрядные версии. Если имеется 32-разрядная установка предыдущей версии SharePoint, а службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установлены в режиме интеграции с SharePoint, то выполнить обновление до SharePoint 2010 будет невозможно. Дополнительные сведения см. в документации по продукту SharePoint.  
  
-   Службы Reporting Services включают надстройку для продуктов SharePoint. Поддерживаемые конфигурации для надстройки и сервера отчетов допускают настройку на более детальном уровне, чем указано здесь. Дополнительные сведения см. в разделе [поддерживаемые сочетания SharePoint и Reporting Services и надстройки &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   Средства разработчика SharePoint поддерживают только изолированную конфигурацию SharePoint.  Дополнительные сведения см. в документации по SharePoint: [Требования по разработке решений SharePoint](https://msdn.microsoft.com/library/ee231582.aspx).  
  
##  <a name="bkmk_vers"></a> Поддержка выпусков SharePoint и компонентов бизнес-Аналитики  
 Некоторые функции бизнес-аналитики [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживаются только в определенных выпусках продуктов SharePoint.  
  
|Поддерживаемые функции|Продукт SharePoint|  
|------------------------|------------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], в состав [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.<br /><br /> Предупреждения об изменении данных в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|Корпоративный выпуск [!INCLUDE[SPS2010](../../includes/sps2010-md.md)].|  
|Общие возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по просмотру отчетов и интеграция функций с SharePoint.|Стандартный и корпоративный выпуск [!INCLUDE[SPS2010](../../includes/sps2010-md.md)].<br /><br /> [!INCLUDE[SPF2010](../../includes/spf2010-md.md)].|  
  
 Дополнительные сведения см. в разделе [функции, поддерживаемые различными выпусками SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_sp1"></a> SharePoint 2010 с пакетом обновления 1 (SP1)  
 Рекомендуется обновить экземпляр SharePoint 2010 до версии SharePoint 2010 с пакетом обновления 1 (SP1). Пакет обновления 1 (SP1) для SharePoint требуется в следующих случаях.  
  
-   Нужно использовать версию [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] компонента Database Engine для баз данных содержимого SharePoint или баз данных каталога служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Нужно использовать [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и средство настройки служб [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Одно из основных причин SP1 является обязательным для установки SharePoint, с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] является компонента database engine **sp_dboption**, который был объявлен устаревшим в предыдущем выпуске, прекращается в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] выпуск. Дополнительные сведения см. в разделе [неподдерживаемые функции ядра СУБД в SQL Server 2014](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)  
  
### <a name="sharepoint-2010-sp1-installation-guidance"></a>Руководство по установке пакета обновления 1 (SP1) для SharePoint 2010  
 [Скачайте SharePoint Server 2010 SP1](https://go.microsoft.com/fwlink/?LinkID=219697) и примените его на всех серверах в ферме.  
  
> [!NOTE]  
>  В существующей ферме, необходимо использовать одно из следующих **дополнительных** обновление действия, чтобы завершить SharePoint с пакетом обновления 1. Дополнительные сведения см. в разделе [известные проблемы при установке пакета обновления 1 для Office 2010 и SharePoint 2010 с пакетом обновления 1](https://support.microsoft.com/kb/2532126) и [описание из SharePoint Server 2010 с пакетом обновления 1](https://support.microsoft.com/kb/2460045):  
  
-   **Мастер настройки продуктов SharePoint:** Запустите мастер для завершения обновления SP1 и конфигурации.  
  
-   **Завершение обновления с помощью psconfig:** Выполните команду `psconfig -upgrade` для завершения обновления SP1  
  
 Дополнительные сведения см. в разделе «обновление» [(SharePoint Server 2010)](https://technet.microsoft.com/library/cc263093.aspx) и [Центр ресурсов: Обновления для продуктов SharePoint 2010](https://technet.microsoft.com/sharepoint/ff800847.aspx)  
  
## <a name="sharepoint-installation-with-sql-server-bi-features"></a>Установка SharePoint с компонентами бизнес-аналитики SQL Server  
  
###  <a name="bkmk_prereq"></a> Средство подготовки продуктов SharePoint 2010  
 Средство подготовки продуктов SharePoint поддерживает роли сервера в операционной системе и устанавливает ПО, необходимое для установки SharePoint. В следующей таблице указаны дополнительные шаги по настройке сервера для служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Компонент|Действие|  
|---------------|------------|  
|Надстройка служб Reporting Services|Средство подготовки продуктов SharePoint 2010 устанавливает версию надстройки служб [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Reporting Services. Службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] содержат новую версию надстроек, необходимых для компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Надстройку можно установить с помощью мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или загрузить с MSDN. Дополнительные сведения о, как получить текущую версию надстройки и его установке см. в разделе [где найти надстройку служб Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md) и [Установка или удаление служб Reporting Services Add-in for SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).|  
|Поставщик OLE DB службы Analysis Services (MSOLAP)|SharePoint 2010 устанавливает версию SQL Server 2008 поставщика OLE DB в составе развернутой службы Excel Services. Эта версия не поддерживает доступ к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Для поддержки подключений к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на серверах SharePoint необходимо установить более позднюю версию этого поставщика. Дополнительные сведения см. в разделе [Установка Analysis Services поставщика OLE DB на серверах SharePoint](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)|  
|Службы ADO.NET|В списке требований SharePoint 2010 указаны службы ADO.NET, но установщик компонентов, необходимых для работы, их не устанавливает. Чтобы добавить службы ADO.NET, их необходимо установить вручную. Установка служб ADO.NET необходима для использования списков SharePoint в качестве веб-каналов данных для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] или отчетов служб Reporting Services. Инструкции см. в разделе [Установка служб данных ADO.NET для поддержки данных экспорта списков SharePoint в виде веб-канала](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).|  
  
###  <a name="bkmk_install"></a> Требования и рекомендации по установке SharePoint  
 Набор устанавливаемых компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и порядок их установки определяет возможные уровни интеграции с SharePoint. Например, на сервере SharePoint со встроенной базой данных доступен определенный уровень интеграции компонентов через службу Reporting Services, но большая часть сценариев интеграции компонентов требует установки фермы SharePoint, так как только ферма предоставляет инфраструктуру, необходимую для работы некоторых компонентов бизнес-аналитики.  
  
 Ферма SharePoint может содержать один или несколько серверов. Ферму отличает от отдельной установки наличие дополнительных компонентов инфраструктуры, таких как служба Claims to Windows Token Service.  
  
 Ферма включается при выборе **фермы серверов** в программе установки SharePoint. Для использования [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] необходимо установить ферму. Изолированная установка SharePoint поддерживается и является типичной в средах разработки для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Однако в рабочей среде рекомендуется устанавливать ферму SharePoint.  
  
 ![GMNI_SetupUI_SharePoint2010InstallType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010installtype.gif "GMNI_SetupUI_SharePoint2010InstallType")  
  
 Для работы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или общей службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] также требуется полная установка сервера.  
  
 ![GMNI_SetupUI_SharePoint2010ServerType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010servertype.gif "GMNI_SetupUI_SharePoint2010ServerType")  
  
 Последняя страница мастера установки предлагает настроить ферму и (необязательно) сконфигурировать веб-приложение по умолчанию и семейство корневых сайтов. Большинство пользователей следуют этому пути установки. Если по какой-либо причине ферма не была настроена, для ее настройки можно использовать вариант настройки фермы в средстве настройки служб [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 В предыдущих выпусках для установки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] рекомендовалось оставлять ферму ненастроенной, поскольку это сокращало число действий, необходимых при использовании параметров установки SQL Server для установки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint в готовом к работе виде. В данном выпуске такой подход потерял актуальность. Средство настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] можно использовать для настройки существующей фермы для использования параметров, рекомендованных для установки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint.  
  
 Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно установить в существующую ферму SharePoint. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и SharePoint можно устанавливать в любом порядке, но конфигурация служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] зависит от порядка установки. Дополнительные сведения см. в разделе [Добавление дополнительного сервера отчетов в ферму &#40;горизонтально масштабируемые службы SSRS&#41; ](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) и [установить службы Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 ![GMNI_SetupUI_DoNotConfigureMOSS](../../../2014/sql-server/install/media/gmni-setupui-donotconfiguremoss.gif "GMNI_SetupUI_DoNotConfigureMOSS")  
  
## <a name="see-also"></a>См. также  
 [Установка и развертывание SharePoint Server 2010](https://technet.microsoft.com/sharepoint/ee518643.aspx)   
 [Несколько серверов для трехуровневой фермы (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834)  
  
  
