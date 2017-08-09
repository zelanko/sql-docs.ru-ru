---
title: "Техническая документация по SQL Server | Документация Майкрософт"
ms.date: 07/31/2017
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
ms.translationtype: HT
ms.sourcegitcommit: b2f5d26757bd436cfd21076b2a4899376ee60c9f
ms.openlocfilehash: 56d4c398f8dc26f00e2d0dc26fb41a3089ea0ebf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/04/2017

---
# <a name="sql-server-technical-documentation"></a>Техническая документация по SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 > Материалы по предыдущим версиям SQL Server см. в статье [Установка SQL Server 2014](https://msdn.microsoft.com/en-US/library/bb500469(SQL.120).aspx).

 Документация по установке, настройке и использованию SQL Server. Материалы включают в себя комплексные примеры, примеры кода и видеоролики. Раздел о языке [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] см. в [справочнике по языку](../t-sql/language-reference.md).

 

**SQL Server 2017**

- [Заметки о выпуске SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)
- [Новые возможности в SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)


**SQL Server 2016**
 
- [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Что нового в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **Оцените SQL Server!**    
 - [![Скачать на странице центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Скачайте [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на странице **[центра оценки](http://go.microsoft.com/fwlink/?LinkID=829477)** 
 - [**Скачайте SQL Server 2016 в центре оценки**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
 - **[Запустите виртуальную машину с уже установленным SQL Server 2016](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    
 - **[Скачайте последнюю версию SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx)**   
      
## <a name="sql-server-technologies"></a>Технологии SQL Server    
    
|||    
|-|-|    
|![Ядро СУБД SQL](../sql-server/media/sql-database-engine.png "Ядро СУБД SQL")|**[Ядро СУБД](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> Компонент ядра СУБД представляет собой основную службу для хранения, обработки и обеспечения безопасности данных. Этот компонент обеспечивает управляемый доступ к ресурсам и быструю обработку транзакций, что позволяет использовать его даже в самых требовательных корпоративных приложениях обработки данных. Кроме того, ядро СУБД предоставляет разносторонние средства поддержания высокого уровня доступности.|    
|![Сервер R](../sql-server/media/r-server.png "Сервер R")|**[Службы машинного обучения](../advanced-analytics/r-services/r-services.md)**<br /><br /> Службы машинного обучения Майкрософт поддерживают интеграцию машинного обучения с рабочими процессами предприятия с помощью популярных языков R и Python.<br /><br /> Службы машинного обучения (в базе данных) интегрируют R и Python с SQL Server, что позволяет легко создавать, повторно обучать и оценивать модели, вызывая хранимые процедуры.<br /><br /> Сервер машинного обучения Майкрософт обеспечивает поддержку корпоративного уровня для R и Python без необходимости использовать SQL Server.|    
|![Службы Data Quality Services](../sql-server/media/data-quality-services.png "Службы Data Quality Services")|**[Службы Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> Службы SQL Server Data Quality Services (DQS) являются решением для очистки данных на основе знаний. Службы DQS позволяют создать базу знаний, а затем выполнить в ней исправление данных и удаление дубликатов с помощью как автоматизированных, так и интерактивных средств. Можно использовать службы справочных данных на основе облачных вычислений, а также создавать решения по управлению данными, где службы DQS будут интегрированы со службами SQL Server Integration Services и Master Data Services.|    
|![Службы Integration Services](../sql-server/media/integration-services.png "Службы Integration Services")|**[Службы Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — это платформа для создания таких высокопроизводительных решений по интеграции данных, как пакеты для хранения данных, которые обеспечивают извлечение, преобразование и загрузку данных.|    
|![Службы Master Data Services](../sql-server/media/master-data-services.png)|**[Службы Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] — это решение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для управления основными данными. Решение, построенное на основе [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , позволяет обеспечить правильность информации, используемой для построения отчетов и выполнения анализа. С помощью [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать центральный репозиторий основных данных и поддерживать запись этих данных по мере их изменения, защищенную и доступную для аудита.|    
|![Службы Analysis Services](../sql-server/media/analysis-services.png "Службы Analysis Services")|**[Службы Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> Службы[!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] — это платформа аналитических данных и набор средств для бизнес-аналитики на личном уровне, уровне рабочей группы и организации. Серверы и клиентские конструкторы поддерживают стандартные решения OLAP, новые решения для создания табличных моделей, а также самостоятельную аналитику и совместную работу с помощью [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], Excel и среды SharePoint Server. Службы[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] также включают интеллектуальный анализ данных, который позволяет выявлять закономерности и связи на основе больших объемов данных.|    
|![Службы репликации](../sql-server/media/replication-services.png "Службы репликации")|**[Репликация](../relational-databases/replication/sql-server-replication.md)**<br /><br /> Репликация представляет собой набор технологий копирования и распространения данных и объектов баз данных между базами данных, а также синхронизации баз данных для поддержания согласованности. Благодаря репликации данные можно размещать в различных местах, обеспечивая возможность доступа к ним удаленных и мобильных пользователей по локальным или глобальным сетям, посредством коммутируемых и беспроводных соединений, а также через Интернет.|    
|![Службы Reporting Services](../sql-server/media/reporting-services.png "Службы Reporting Services")|**[Службы Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Службы Reporting Services предлагают средства создания корпоративных отчетов с поддержкой веб-интерфейса, которые позволяют включать в отчеты данные из различных источников, публиковать отчеты в разнообразных форматах, а также централизованно управлять безопасностью и подписками.|    

    
## <a name="earlier-sql-server-versions"></a>Предыдущие версии SQL Server
- [Электронная документация по электронной документации по SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
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
+ Документацию по SQL Server можно также просмотреть в автономном режиме с помощью окна справки. Дополнительные сведения см. в статье [Окно справки и автономное содержимое для SQL Server](../release-notes/sql-server-help-installation.md).
+ [Диспетчер конфигурации SQL Server](../relational-databases/sql-server-configuration-manager.md)
+ Ссылки и сведения для всех поддерживаемых версий в[Центре обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx)  
+ [Установка ядра СУБД SQL Server](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [Установка средств управления SQL Server со средой SSMS](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [SQL Server Data Tools в Visual Studio 2015](https://msdn.microsoft.com/mt186501.aspx)
+ [Видеоролики, примеры и ресурсы сообщества](https://msdn.microsoft.com/library/dn237258.aspx)
  
##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql сервера) — задавайте технические вопросы](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN — задавайте технические вопросы](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по SQL Server](https://www.reddit.com/r/SQLServer/)
