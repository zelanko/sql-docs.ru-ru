---
title: "Техническая документация по SQL Server | Документы Microsoft"
ms.date: 03/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.portal.f1
helpviewer_keywords:
- documentation [SQL Server], home page
- Help [SQL Server]
- SQL Server, documentation
- home page [SQL Server]
- Help [SQL Server], documentation home page
- Books Online [SQL Server], home page
- portal page [SQL Server]
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: 106
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 6ba40fbd036ee6476d7eb3439a5d9e816e79651d
ms.contentlocale: ru-ru
ms.lasthandoff: 05/25/2017

---
# <a name="sql-server-technical-documentation"></a>Техническая документация по SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 > Содержимое, связанное с предыдущих версий SQL Server, в разделе [установки для SQL Server 2014](https://msdn.microsoft.com/en-US/library/bb500469(SQL.120).aspx).

 Документация по установке, настройке и использованию SQL Server. Материалы включают в себя комплексные примеры, примеры кода и видеоролики. Раздел о языке [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] см. в [справочнике по языку](../t-sql/language-reference.md).

**SQL Server 2017 г.**

- [Заметки о выпуске SQL Server 2017 г.](../sql-server/sql-server-2017-release-notes.md)
- [Новые возможности SQL Server 2017 г.](../sql-server/what-s-new-in-sql-server-2017.md)
 
**SQL Server 2016:**
 
- [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Что нового в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **Оцените SQL Server!**    
 - [**Download SQL Server 2016  from the Evaluation Center**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
 - **[Запустите виртуальную машину с уже установленным SQL Server 2016](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**.    
 - **[Download the latest version of SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**   
      
## <a name="sql-server-technologies"></a>Технологии SQL Server    
    
|||    
|-|-|    
|![Ядро СУБД SQL](../sql-server/media/sql-database-engine.png "Ядро СУБД SQL")|**[Ядро СУБД](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> Компонент ядра СУБД представляет собой основную службу для хранения, обработки и обеспечения безопасности данных. Этот компонент обеспечивает управляемый доступ к ресурсам и быструю обработку транзакций, что позволяет использовать его даже в самых требовательных корпоративных приложениях обработки данных. Кроме того, ядро СУБД предоставляет разносторонние средства поддержания высокого уровня доступности.|    
|![Сервер R](../sql-server/media/r-server.png "Сервер R")|**[Службы R Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Службы Microsoft R Services предоставляют несколько способов внедрения популярного языка R в рабочие процессы предприятия.<br /><br /> [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] интегрирует язык R с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], упрощая создание, повторное обучение и оценку моделей с помощью вызова хранимых процедур [!INCLUDE[tsql](../includes/tsql-md.md)] .<br /><br /> Microsoft R Server обеспечивает мультиплатформенную, масштабируемую поддержку R на предприятии, а также поддерживает такие источники данных, как Hadoop и Teradata.|    
|![Службы Data Quality Services](../sql-server/media/data-quality-services.png "Службы Data Quality Services")|**[Службы Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> Службы SQL Server Data Quality Services (DQS) являются решением для очистки данных на основе знаний. Службы DQS позволяют создать базу знаний, а затем выполнить в ней исправление данных и удаление дубликатов с помощью как автоматизированных, так и интерактивных средств. Можно использовать службы справочных данных на основе облачных вычислений, а также создавать решения по управлению данными, где службы DQS будут интегрированы со службами SQL Server Integration Services и Master Data Services.|    
|![Службы Integration Services](../sql-server/media/integration-services.png "Службы Integration Services")|**[Службы Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — это платформа для создания таких высокопроизводительных решений по интеграции данных, как пакеты для хранения данных, которые обеспечивают извлечение, преобразование и загрузку данных.|    
|![Службы Master Data Services](../sql-server/media/master-data-services.png)|**[Службы Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] — это решение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для управления основными данными. Решение, построенное на основе [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , позволяет обеспечить правильность информации, используемой для построения отчетов и выполнения анализа. С помощью [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать центральный репозиторий основных данных и поддерживать запись этих данных по мере их изменения, защищенную и доступную для аудита.|    
|![Службы Analysis Services](../sql-server/media/analysis-services.png "Службы Analysis Services")|**[Службы Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> Службы[!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] — это платформа аналитических данных и набор средств для бизнес-аналитики на личном уровне, уровне рабочей группы и организации. Серверы и клиентские конструкторы поддерживают стандартные решения OLAP, новые решения для создания табличных моделей, а также самостоятельную аналитику и совместную работу с помощью [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], Excel и среды SharePoint Server. Службы[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] также включают интеллектуальный анализ данных, который позволяет выявлять закономерности и связи на основе больших объемов данных.|    
|![Службы репликации](../sql-server/media/replication-services.png "Службы репликации")|**[Репликация](../relational-databases/replication/sql-server-replication.md)**<br /><br /> Репликация представляет собой набор технологий копирования и распространения данных и объектов баз данных между базами данных, а также синхронизации баз данных для поддержания согласованности. Благодаря репликации данные можно размещать в различных местах, обеспечивая возможность доступа к ним удаленных и мобильных пользователей по локальным или глобальным сетям, посредством коммутируемых и беспроводных соединений, а также через Интернет.|    
|![Службы Reporting Services](../sql-server/media/reporting-services.png "Службы Reporting Services")|**[Службы Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Службы Reporting Services предлагают средства создания корпоративных отчетов с поддержкой веб-интерфейса, которые позволяют включать в отчеты данные из различных источников, публиковать отчеты в разнообразных форматах, а также централизованно управлять безопасностью и подписками.|    

    
## <a name="earlier-sql-server-versions"></a>Предыдущие версии SQL Server
- [Электронная документация по электронной документации по SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
- [Установка SQL Server 2014 Express и других, более ранних версий SQL Server](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx). (**Выражаем благодарность [Скотту Хэнсельману](http://www.hanselman.com/) (Scott Hanselman) за сбор всех ссылок на пакеты установщика**.)  
- [Техническая документация по SQL Server 2012](https://technet.microsoft.com/library/bb418433(v=sql.10).aspx)  
- [Документация по SQL Server 2008 R2](https://msdn.microsoft.com/library/hh278298(v=sql.10).aspx)  
- [Техническая документация по SQL Server 2008](https://msdn.microsoft.com/library/hh994727(v=sql.10).aspx) 
- [Архивная документация по SQL Server 2005](https://msdn.microsoft.com/library/hh278313(v=sql.10).aspx)    

**Образцы баз данных**  
- [Образец базы данных Wide World Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx)  
- [Образцы баз данных AdventureWorks и скрипты для SQL Server 2016](https://www.microsoft.com/en-us/download/details.aspx?id=49502) 
- [Образцы SQL Server на GitHub](https://github.com/Microsoft/sql-server-samples) 
   
 ## <a name="more-information"></a>Дополнительные сведения   
+ [Диспетчер конфигурации SQL Server](../relational-databases/sql-server-configuration-manager.md)
+ Ссылки и сведения для всех поддерживаемых версий в[Центре обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx)  
+ [Установка ядра СУБД SQL Server](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [Установка средств управления SQL Server со средой SSMS](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [SQL Server Data Tools в Visual Studio 2015](https://msdn.microsoft.com/mt186501.aspx)
+ [Видеоролики, примеры и ресурсы сообщества](https://msdn.microsoft.com/library/dn237258.aspx)
  
[!INCLUDE[feedback_stackoverflow_msdn_connect-md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

