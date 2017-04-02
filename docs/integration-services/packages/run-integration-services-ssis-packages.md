---
title: "Запуск пакетов служб Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты служб Integration Services, запуск"
  - "пакеты служб SSIS, выполнение"
  - "пакеты [службы Integration Services], выполняемые"
  - "пакеты служб SQL Server Integration Services, выполнение"
  - "запуск пакетов [службы Integration Services]"
  - "запуск пакетов [службы Integration Services]"
  - "службы Integration Services,(см. также пакеты служб Integration Services)"
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
caps.latest.revision: 65
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Запуск пакетов служб Integration Services (SSIS)
  Чтобы запустить пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , можно воспользоваться одним из предостовляемых средств. Выбор средства зависит от места хранения пакета. Эти средства приведены в следующей таблице.  
  
 Чтобы сохранить пакет на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , используется модель развертывания проекта. Дополнительные сведения см. в разделе [Deploy Projects to Integration Services Server](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 Чтобы сохранить пакет в хранилище пакетов SSIS, базе данных msdb, или в файловой системе, используется модель развертывания пакета. Дополнительные сведения см. в разделе [Устаревшее развертывание пакетов (службы SSIS)](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
|Инструмент|Пакеты, хранимые на сервере служб Integration Services|Пакеты, которые находятся в хранилище пакетов служб SSIS предыдущих версий или в базе данных msdb.|Пакеты, хранимые в файловой системе вне расположения входящего в состав хранилища пакетов SSIS.|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|Нет|Нет<br /><br /> Однако существующий пакет можно добавить в проект из хранилища пакетов [!INCLUDE[ssIS](../../includes/ssis-md.md)] , включающего в себя базу данных msdb. При добавлении существующего пакета в проект таким методом локальная копия пакета создается в файловой системе.|Да|  
|**В среде SQL Server Management Studio, если установлено соединение с экземпляром ядра СУБД, где размещен сервер служб Integration Services.**<br /><br /> Дополнительные сведения см. в разделе [Execute Package Dialog Box](../../integration-services/packages/execute-package-dialog-box.md).|Да|Нет<br /><br /> Однако из этих расположений пакет можно импортировать на сервер.|Нет<br /><br /> Однако пакет можно импортировать на сервер из файловой системы.|
|**В среде SQL Server Management Studio, если установлено соединение с экземпляром ядра СУБД, где размещен сервер служб Integration Services, заданный в качестве мастера масштабирования.**<br /><br /> Дополнительные сведения см. в статье [Execute packages in Scale Out](../../integration-services/run-packages-in-integration-services-ssis-scale-out.md) (Выполнение пакетов при масштабном развертывании).|Да|Нет|Нет|
|**В среде SQL Server Management Studio, если установлено соединение со службами Integration Services, управляющими хранилищем пакетов служб SSIS.**|Нет|Да|Нет<br /><br /> Однако пакет можно импортировать в хранилище пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] из файловой системы.|  
|**dtexec**<br /><br /> Дополнительные сведения см. в статье [dtexec Utility](../../integration-services/packages/dtexec-utility.md).|Да|Да|Да|  
|**dtexecui**<br /><br /> Дополнительные сведения см. в разделе [Справочник по пользовательскому интерфейсу программы выполнения пакетов (DtExecUI)](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md).|Нет|Да|Да|  
|**Агент SQL Server**<br /><br /> Чтобы запланировать запуск пакета, используйте задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Дополнительные сведения см. в статье [SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).|Да|Да|Да|  
|**Встроенная хранимая процедура**<br /><br /> Дополнительные сведения см. в разделе [catalog.start_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).|Да|Нет|Нет|  
|**Управляемый API-интерфейс, используя типы и элементы из пространства имен** <xref:Microsoft.SqlServer.Management.IntegrationServices> |Да|Нет|Нет|  
|**Управляемый API-интерфейс, используя типы и элементы из пространства имен** <xref:Microsoft.SqlServer.Dts.Runtime> |В настоящее время нет|Да|Да|  
  
## <a name="execution-and-logging"></a>Выполнение и ведение журнала  
 Данные о пакетах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут заноситьтся в журнал выполнения, данные времени исполнения могут сохраняться в файлах журнала. Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
 С помощью отчетов о выполнении можно отслеживать пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , развернутые и выполняемые на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Отчеты доступны в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Планирование пакета с помощью агента SQL Server](../../integration-services/packages/schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Запуск пакета с помощью SQL Server Data Tools](../../integration-services/packages/run-a-package-in-sql-server-data-tools.md)  
  
-   [Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Программа dtexec](../../integration-services/packages/dtexec-utility.md)   
[Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)
  
  