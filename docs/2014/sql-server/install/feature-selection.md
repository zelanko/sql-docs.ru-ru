---
title: Выбор компонентов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- feature selection, Setup
helpviewer_keywords:
- SQL Server Installation Wizard, Components to Install page
- Components to Install page [SQL Server Installation Wizard]
ms.assetid: 73182088-153b-4634-a060-d14d1fd23b70
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ec5bf4706f349a4e0aabb254b4ac74f9d396128d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065397"
---
# <a name="feature-selection"></a>Выбор компонентов
  С помощью флажков на странице **Выбор компонентов** мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите компоненты для текущей установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="installing-ssnoversion-features"></a>Установка компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 На странице **Выбор компонентов** компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разделены на два основных раздела. **Компоненты экземпляра** и **Общие компоненты**.  
  
 Раздел**Компоненты экземпляра** содержит список компонентов, которые устанавливаются отдельно для каждого экземпляра. Каждый экземпляр может иметь отдельную версию, имеющую свой уровень обновления. При установке обновления, вне зависимости от того, является ли оно пакетом обслуживания, исправлением или накопительным обновлением, выполняется обновление только одного экземпляра, размещенного на конкретном компьютере, а также общих компонентов, если они еще не обновлены.  
  
 Термин**Общие компоненты** относится к компонентам, которые являются общими для всех экземпляров на данном компьютере. Каждый из этих общих компонентов создается с учетом требований обратной совместимости с поддерживаемыми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (пакеты обновления, накопительные обновления, пакеты обслуживания и исправления), которые можно установить параллельно.  
  
> [!NOTE]  
>  ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Отказоустойчивые кластеры.** [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] компоненты и являются единственными [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] функциями, поддерживающими отказоустойчивую кластеризацию. На узел отказоустойчивого кластера можно установить другие компоненты, такие как службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], но они не предназначены для работы в кластере, и их службы не переходят на резервный ресурс, если узел отказоустойчивого кластера переходит в автономный режим. Дополнительные сведения см. в разделе [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](../failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
### <a name="instance-features"></a>Компоненты экземпляра  
 Описание каждой группы компонентов отображается на панели **Описание** при выборе соответствующей группы. Можно установить любое сочетание компонентов (устанавливаемые компоненты отмечаются флажками). Чтобы продолжить установку, выберите компоненты.  
  
|Компоненты|Описание|  
|--------------|-----------------|  
|Службы[!INCLUDE[ssDE](../../includes/ssde-md.md)]|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]включает компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] , основную службу для хранения, обработки и защиты данных, репликацию, полнотекстовый поиск, средства управления реляционными и XML-данными, а также [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] сервер (DQS). Ниже перечислены функции ядра СУБД:<br /><br /> [!INCLUDE[ssDE](../../includes/ssde-md.md)] — основная служба для хранения, обработки и защиты данных.<br /><br /> Репликация: Необязательно. Репликация представляет собой набор технологий копирования и распространения данных и объектов баз данных между базами данных, а также синхронизации баз данных для поддержания согласованности.<br /><br /> Полнотекстовый поиск. Необязательно. Компонент Full-Text Search позволяет выполнять полнотекстовые запросы в таблицах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для произвольных символьных данных.<br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]: Необязательно. [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) — это решение для очистки данных, которое позволяет обнаруживать непоследовательные и неверные данные в источнике данных, а также предоставляет возможность для очистки данных в интерактивных и компьютерных целях. Выберите этот флажок, чтобы установить сервер DQS. После завершения установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо запустить файл DQSInstaller.exe, чтобы *завершить* установку сервера DQS. Если установлен экземпляр SQL Server по умолчанию, этот файл доступен в папке C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. мссклсервер\мсскл\бинн.<br /><br /> <br /><br /> ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Отказоустойчивые кластеры.** компоненты для репликации и полнотекстового поиска являются обязательными и автоматически выбираются программой установки для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки отказоустойчивой кластеризации при выборе ядро СУБД Services.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] содержит средства создания приложений оперативной аналитической обработки (OLAP) и приложений интеллектуального анализа данных, а также средства управления ими.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]— Native|Собственный режим служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует серверные и клиентские компоненты для создания и развертывания табличных, матричных и графических отчетов и отчетов в свободной форме, а также управления ими. Службы[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] являются расширяемой платформой, которую можно использовать для разработки приложений отчетов.|  
  
> [!IMPORTANT]
>  1.  Программа установки не настраивает балансировку нагрузки и адресацию по одному URL-адресу для нескольких узлов при масштабном развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Для завершения масштабного развертывания необходимы Windows Server, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Application Center или программное обеспечение сторонних разработчиков для управления кластером. Дополнительные сведения о настройке развертывания веб-фермы см. в разделе [настройка Reporting Services для масштабного развертывания](https://go.microsoft.com/fwlink/?LinkId=199448) ( https://go.microsoft.com/fwlink/?LinkId=199448) .  
> 2.  Требования к браузеру компонентов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в разделе [Планирование служб Reporting Services и поддержки Power View в браузерах (Reporting Services 2014)](../../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).  
> 3.  Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не поддерживаются в параллельных конфигурациях на 64-разрядной платформе и в 32-разрядной подсистеме (WOW64) 64-разрядного сервера.  
  
### <a name="shared-features"></a>Общие функции  
 Компоненты, совместно используемые всеми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на одном компьютере, устанавливаются в один и тот же каталог. Среди них:  
  
|Компонент|Описание|  
|-------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — SharePoint|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Режим интеграции с SharePoint — это серверное приложение, предназначенное для создания, управления и доставки отчетов по электронной почте, в нескольких форматах файлов и интерактивных веб-форм. В режиме SharePoint функции просмотра отчетов и управления ими интегрированы в продукты SharePoint. Дополнительные сведения см. в разделе [Сервер отчетов служб Reporting Services (режим SharePoint)](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md).|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint|Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint содержит компоненты пользовательского интерфейса и средства управления, позволяющие интегрировать продукт SharePoint с сервером отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], работающим в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [где найти надстройку Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
|Клиент Data Quality|Data Quality Client — это отдельное приложение, которое подключается к серверу DQS и обеспечивает интуитивный графический пользовательский интерфейс для очистки данных, выполнения операций подбора данных и административных задач в DQS.|  
|Средства связи клиентских средств|В клиентские средства входят компоненты, предназначенные для обеспечения взаимодействия между клиентами и серверами, в том числе сетевые библиотеки для DB-Library, OLEDB для OLAP, ODBC, ADODB и ADOMD+.|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] представляют собой набор графических средств и программируемых объектов для перемещения, копирования и преобразования данных.|  
|Обратная совместимость клиентских средств|Обратная совместимость клиентских средств обеспечивается следующими компонентами.<br /><br /> Объекты SQL-DMO. Дополнительные сведения см. в разделе [Discontinued SQL Server Features in SQL Server 2014](../../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md).<br /><br /> Объекты DSO. Дополнительные сведения см. в разделе [Breaking Changes to Analysis Services Features in SQL Server 2014](../../../2014/analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2014.md).|  
|Пакет SDK клиентских средств|Содержит пакет средств разработки программного обеспечения, содержащий ресурсы для программистов.|  
|Компоненты документации|Компоненты документации содержат компоненты для просмотра и управления содержимым справки.|  
|Основные средства управления|**Средства управления — базовый:** Сюда входят следующие:<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]поддержка [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , программы **sqlcmd** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика PowerShell<br /><br /> **Средства управления — полный комплекс:** Сюда входят следующие компоненты, а также компоненты базовой версии.<br /><br /> Поддержка среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<br /><br /> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<br /><br /> Database Engine Tuning Advisor<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Управление программой|  
|Контроллер распределенного воспроизведения|Контроллер распределенного воспроизведения управляет согласованными действиями клиентов распределенного воспроизведения. В каждой среде распределенного воспроизведения можно установить только один экземпляр контроллера. Дополнительные сведения см. в статье [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).|  
|Клиент распределенного воспроизведения|Клиенты распределенного воспроизведения работают совместно для имитации рабочей нагрузки на экземпляре SQL Server. В каждой среде распределенного воспроизведения можно установить один или несколько клиентов. Дополнительные сведения см. в статье [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).|  
|Пакет SDK для подключения клиентов SQL|Содержит пакет SDK для подключения собственных клиентов Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ODBC/OLE DB) для разработки приложений баз данных.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|Службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] — это платформа для интеграции данных из различных систем на предприятии в единый источник основных данных для повышения точности и удобной организации аудита. При выборе параметра [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] устанавливается [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], сборки, оснастка Windows PowerShell, папки и файлы для веб-приложений и служб.|  
  
 По умолчанию общие компоненты устанавливаются в каталог %Program Files%Microsoft SQL Server\\. Чтобы изменить путь установки, нажмите кнопку **Обзор** . Изменение пути установки для одного общего компонента приводит к его изменению для всех остальных общих компонентов. При последующей установке общие компоненты устанавливаются в каталог, заданный при начальной установке.  
  
 **Корневой каталог экземпляра** — по умолчанию корневым каталогом экземпляра является C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \\ . Для указания корневого каталога, отличного от заданного по умолчанию, введите его путь или нажмите кнопку **Обзор** .  
  
 В операционных системах для компьютеров с процессорами x64 места установки 64-разрядных компонентов и 32-разрядных компонентов подсистемы WOW64 можно выбрать раздельно.  
  
## <a name="disk-space-requirements"></a>Требования к месту на диске  
 На странице «Сведение о месте на диске» приводится информация о необходимом дисковом пространстве для компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выбранных для установки.  
  
### <a name="options"></a>Варианты  
 Если требуемое место на диске слишком велико, можно:  
  
-   изменить каталоги установки на диск, где больше свободного места;  
  
-   изменить компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки;  
  
-   освободить больше места на выбранном диске, переместив другие файлы или приложения.  
  
## <a name="installing-adventureworks-sample-databases"></a>Установка образцов баз данных AdventureWorks  
 По умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы баз данных и образцы кода не устанавливаются. Дополнительные сведения об установке образцов баз данных и примеров кода см. в разделе [Microsoft SQL Server проектов сообщества & Samples](https://go.microsoft.com/fwlink/?LinkId=87843) ( https://go.microsoft.com/fwlink/?LinkId=87843) .  
  
 Дополнительные сведения об образцах доступны после завершения установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . В меню **Пуск** последовательно выберите пункты **все программы**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** , **Документация и учебные материалы**, а затем — ** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Обзор образцов**.  
  
## <a name="see-also"></a>См. также:  
 [Выпуски и компоненты SQL Server 2014](../editions-and-components-of-sql-server-2016.md)  
  
  
