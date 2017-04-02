---
title: "Новые возможности в SQL Server vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: "craigg-msft"
ms.author: "craigg"
manager: "jhubbard"
caps.handback.revision: 65
---
# Новые возможности в SQL Server vNext
SQL Server vNext представляет собой важный шаг к созданию платформы SQL Server, которая обеспечивает выбор языков разработки, типов данных, локальных и облачных сред, а также операционных систем за счет привнесения функций SQL Server в Linux, контейнеры Docker для Linux и Windows.

В этом разделе приводится сводка новых возможностей в последней ознакомительной версии для сообщества (CTP), а также ссылки на более подробные сведения о новых возможностях в определенных областях.

![info_tip](../sql-server/media/info-tip.png) Запуск SQL Server в Linux Дополнительные сведения см. в разделе:
-  [Новые возможности SQL Server vNext в Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-whats-new)
-  [Документация по SQL Server на платформе Linux](https://docs.microsoft.com/en-us/sql/linux/)


**Попробуйте продукт:**    
   -   [![Скачать на странице центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Скачайте ознакомительную версию для сообщества SQL Server vNext](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="whats-new-in-sql-server-vnext-ctp-13-february-2017"></a>Новые возможности в SQL Server vNext CTP 1.3 (февраль 2017 г.)
### <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine
- Повышена производительность косвенных контрольных точек.
- Добавлена поддержка групп доступности без кластеризации.
- Добавлен параметр групп доступности для фиксации минимальных реплик.
- Теперь группы доступности могут работать как в Windows, так и в Linux, что обеспечивает возможность кроссплатформенной миграции и тестирования.
- Добавлена поддержка политики хранения темпоральных таблиц.
- Реализовано новое динамическое административное представление SYS.DM_DB_STATS_HISTOGRAM.
- Добавлена поддержка сборки и перестройки некластеризованного индекса columnstore в Интернете.
- Реализованы пять новых динамических административных представлений для возврата данных о процессе Linux. Дополнительные сведения см. в статье [Динамические административные представления процессов Linux (Transact-SQL)](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- Добавлено представление [sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) для проверки статистики.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>Службы SQL Server Analysis Services (SSAS) (CTP 1.3)
- Подсказки службы кодирования — расширенная функция, использующаяся для оптимизации обработки (обновления данных) больших табличных моделей в памяти. Дополнительные сведения см. в статье [Новые возможности служб SQL Server Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md). 

## <a name="whats-new-in-sql-server-vnext-ctp-12-january-2017"></a>Новые возможности в SQL Server vNext CTP 1.2 (январь 2017 г.)
### <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine
- Поддержка сборки и перестройки некластеризованных индексов columnstore в Интернете.
- Эта CTP-версия также содержит исправления ошибок для ядра СУБД.
- Подробный список улучшений в CTP-версии vNext в предыдущих выпусках CTP см. в статье [Новые возможности в SQL Server vNext (ядро СУБД)](../database-engine/configure-windows/what-s-new-in-sql-server-vnext-database-engine.md).

### <a name="sql-server-r-services"></a>Службы R SQL Server
- В этой CTP-версии нет новых функций служб R.
- Более подробные сведения о новых возможностях служб R, включая сведения для предыдущих CTP-версий, см. в разделе [Новые возможности служб SQL Server R Services](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>Службы SQL Server Reporting Services (SSRS)
- В этой CTP-версии нет новых функций служб SSRS.
- Более подробные сведения о новых возможностях SSRS, включая сведения из предыдущих выпусков, см. в статье [Новые возможности служб Reporting Services (SSRS)](../reporting-services/новые-возможности-служб-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>Службы SQL Server Analysis Services (SSAS)
- В этой CTP-версии нет новых функций SSAS.  
- Дополнительные сведения см. в разделе [Новые возможности в службах Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md).  

### <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services
- В этой CTP-версии нет новых функций служб SQL Server Integration Services.
- Более подробные сведения о новых возможностях служб SQL Server Integration Services, включая сведения для предыдущих CTP-версий, см. в разделе [Новые возможности в службах Integration Services vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md).  

### <a name="master-data-services-mds"></a>Службы Master Data Services (MDS)
- В этой CTP-версии нет новых функций служб Master Data Services.

##  <a name="infotipimageshiproominfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по поводу R](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>См. также:    
 + [![Заметки о выпуске](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png)](SQL%20Server%20vNext%20Release%20Notes.md)[ SQL Server VNext](../sql-server/sql-server-vnext-release-notes.md). 
+ [Возможности, поддерживаемые различными выпусками](https://msdn.microsoft.com/library/cc645993.aspx)
 + [[Требования к оборудованию и программному обеспечению для установки](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)](Hardware%20and%20Software%20Requirements%20for%20Installing%20SQL%20Server%202016.md)
 + [Мастер установки](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)
 
 + [Настройка и обслуживание установки](Setup%20and%20Servicing%20Installation.md)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)