---
title: "Техническая документация SQL Server 2016 | Microsoft Docs"
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.portal.f1"
helpviewer_keywords: 
  - "документация [SQL Server], домашняя страница"
  - "Help [SQL Server]"
  - "SQL Server, documentation"
  - "домашняя страница [SQL Server]"
  - "Справка [SQL Server], домашняя страница документации"
  - "Электронная документация [SQL Server], домашняя страница"
  - "страница портала [SQL Server]"
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: 106
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Техническая документация по SQL Server
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

 Документация по установке, настройке и использованию SQL Server. Материалы включают в себя комплексные примеры, примеры кода и видеоролики. Раздел о языке [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] см. в [справочнике по языку](../t-sql/language-reference.md).

**SQL Server vNext**

Заметки о последнем выпуске см. в разделе [Заметки о выпуске SQL Server vNext](../sql-server/sql-server-vnext-release-notes.md).

Актуальные сведения о новых возможностях см. в разделе [Что нового в SQL Server vNext](../sql-server/what-s-new-in-sql-server-vnext.md).
 
**SQL Server 2016:**
 
 [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)

[Что нового в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **Оцените SQL Server!**    
    
 - [**Скачайте SQL Server 2016 в центре оценки**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016).    
    
- **[Запустите виртуальную машину с уже установленным SQL Server 2016](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**.    
    
-  **[Скачайте последнюю версию SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**.   
    
  
    
## <a name="sql-server-technologies"></a>Технологии SQL Server    
    
|||    
|-|-|    
|![SQL database engine](../sql-server/media/sql-database-engine.png "SQL database engine")|**[Ядро СУБД](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> Компонент ядра СУБД представляет собой основную службу для хранения, обработки и обеспечения безопасности данных. Этот компонент обеспечивает управляемый доступ к ресурсам и быструю обработку транзакций, что позволяет использовать его даже в самых требовательных корпоративных приложениях обработки данных. Кроме того, компонент Database Engine предоставляет разносторонние средства поддержания высокого уровня доступности.|    
|![R Server](../sql-server/media/r-server.png "R Server")|**[Службы R Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Службы Microsoft R Services предоставляют несколько способов внедрения популярного языка R в рабочие процессы предприятия.<br /><br /> [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] интегрирует язык R с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], упрощая создание, повторное обучение и оценку моделей с помощью вызова хранимых процедур [!INCLUDE[tsql](../includes/tsql-md.md)].<br /><br /> Microsoft R Server обеспечивает мультиплатформенную, масштабируемую поддержку R на предприятии, а также поддерживает такие источники данных, как Hadoop и Teradata.|    
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Службы Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> Службы SQL Server Data Quality Services (DQS) являются решением для очистки данных на основе знаний. Службы DQS позволяют создать базу знаний, а затем выполнить в ней исправление данных и удаление дубликатов с помощью как автоматизированных, так и интерактивных средств. Можно использовать службы справочных данных на основе облачных вычислений, а также создавать решения по управлению данными, где службы DQS будут интегрированы со службами SQL Server Integration Services и Master Data Services.|    
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Службы Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — это платформа для создания таких высокопроизводительных решений по интеграции данных, как пакеты для хранения данных, которые обеспечивают извлечение, преобразование и загрузку данных.|    
|![Службы Master Data Services](../sql-server/media/master-data-services.png)|**[Службы Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] — это решение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для управления основными данными. Решение, построенное на основе [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , позволяет обеспечить правильность информации, используемой для построения отчетов и выполнения анализа. С помощью [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать центральный репозиторий основных данных и поддерживать запись этих данных по мере их изменения, защищенную и доступную для аудита.|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Службы Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> Службы [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] — это платформа аналитических данных и набор средств для бизнес-аналитики на личном уровне, уровне рабочей группы и организации. Серверы и клиентские конструкторы поддерживают стандартные решения OLAP, новые решения для создания табличных моделей, а также самостоятельную аналитику и совместную работу с помощью [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], Excel и среды SharePoint Server. Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] также включают интеллектуальный анализ данных, который позволяет выявлять закономерности и связи на основе больших объемов данных.|    
|![Replication services](../sql-server/media/replication-services.png "Replication services")|**[Репликация](../relational-databases/replication/sql-server-replication.md)**<br /><br /> Репликация представляет собой набор технологий копирования и распространения данных и объектов баз данных между базами данных, а также синхронизации баз данных для поддержания согласованности. Благодаря репликации данные можно размещать в различных местах, обеспечивая возможность доступа к ним удаленных и мобильных пользователей по локальным или глобальным сетям, посредством коммутируемых и беспроводных соединений, а также через Интернет.|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Службы Reporting Services](../reporting-services/reporting-services-ssrs.md)**<br /><br /> Службы Reporting Services предлагают средства создания корпоративных отчетов с поддержкой веб-интерфейса, которые позволяют включать в отчеты данные из различных источников, публиковать отчеты в разнообразных форматах, а также централизованно управлять безопасностью и подписками.|    
     
   
 ## <a name="more-information"></a>Дополнительные сведения   
+ [Диспетчер конфигурации SQL Server](../relational-databases/sql-server-configuration-manager.md)
+ Ссылки и сведения для всех поддерживаемых версий в [Центре обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) 
+ [Установка ядра СУБД SQL Server](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [Установка средств управления SQL Server со средой SSMS](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [SQL Server Data Tools в Visual Studio 2015](https://msdn.microsoft.com/mt186501.aspx)
+ [Видеоролики, примеры и ресурсы сообщества](https://msdn.microsoft.com/library/dn237258.aspx)
+ [Знакомство с SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server/default.aspx?WT.srch=1&WT.mc_id=SEM_%5B_uniqid%5D&utm_source=Bing&utm_medium=CPC&utm_term=SQL%20Server%202016&utm_campaign=Data_Management)  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect-md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
