---
title: Запуск проектов и пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
- executing packages [Integration Services]
- running packages [Integration Services]
- Integration Services, (See also Integration Services packages)
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b54c533fd86c780f69583acc2a329d7f348502c7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52799008"
---
# <a name="execution-of-projects-and-packages"></a>Запуск проектов и пакетов
  Чтобы запустить пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , можно воспользоваться одним из предостовляемых средств. Выбор средства зависит от места хранения пакета. Эти средства приведены в следующей таблице.  
  
 Чтобы сохранить пакет на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , используется модель развертывания проекта. Дополнительные сведения см. в разделе [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).  
  
 Чтобы сохранить пакет в хранилище пакетов SSIS, базе данных msdb, или в файловой системе, используется модель развертывания пакета. Дополнительные сведения см. в разделе [развертывания пакета &#40;SSIS&#41;](legacy-package-deployment-ssis.md).  
  
|Инструмент|Пакеты, хранимые на сервере служб Integration Services|Пакеты, которые находятся в хранилище пакетов служб SSIS предыдущих версий или в базе данных msdb.|Пакеты, хранимые в файловой системе вне расположения входящего в состав хранилища пакетов SSIS.|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|нет|нет<br /><br /> Однако существующий пакет можно добавить в проект из хранилища пакетов [!INCLUDE[ssIS](../../includes/ssis-md.md)] , включающего в себя базу данных msdb. При добавлении существующего пакета в проект таким методом локальная копия пакета создается в файловой системе.|Да|  
|**В среде SQL Server Management Studio, если установлено соединение с экземпляром ядра СУБД, где размещен сервер служб Integration Services.**<br /><br /> Дополнительные сведения см. в разделе [Execute Package Dialog Box](../execute-package-dialog-box.md).|Да|нет<br /><br /> Однако из этих расположений пакет можно импортировать на сервер.|нет<br /><br /> Однако пакет можно импортировать на сервер из файловой системы.|  
|**В среде SQL Server Management Studio, если установлено соединение со службами Integration Services, управляющими хранилищем пакетов служб SSIS.**|нет|Да|нет<br /><br /> Однако пакет можно импортировать в хранилище пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] из файловой системы.|  
|**dtexec**<br /><br /> Дополнительные сведения см. в статье [dtexec Utility](dtexec-utility.md).|Да|Да|Да|  
|**dtexecui**<br /><br /> Дополнительные сведения см. в разделе [Справочник по пользовательскому интерфейсу программы выполнения пакетов (DtExecUI)](execute-package-utility-dtexecui-ui-reference.md).|нет|Да|Да|  
|**Агент SQL Server**<br /><br /> Чтобы запланировать запуск пакета, используйте задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Дополнительные сведения см. в статье [SQL Server Agent Jobs for Packages](sql-server-agent-jobs-for-packages.md).|Да|Да|Да|  
|**Встроенная хранимая процедура**<br /><br /> Дополнительные сведения см. в разделе [catalog.start_execution (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).|Да|Нет|нет|  
|**Управляемые API, использующие типы и элементы пространства имен** <xref:Microsoft.SqlServer.Management.IntegrationServices>|Да|Нет|нет|  
|**Управляемые API, использующие типы и элементы пространства имен** <xref:Microsoft.SqlServer.Dts.Runtime>|В настоящее время нет|Да|Да|  
  
## <a name="execution-and-logging"></a>Выполнение и ведение журнала  
 Данные о пакетах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут заноситьтся в журнал выполнения, данные времени исполнения могут сохраняться в файлах журнала. Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md).  
  
 С помощью отчетов о выполнении можно отслеживать пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , развернутые и выполняемые на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Отчеты доступны в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Планирование пакета с помощью агента SQL Server](../schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Запуск пакета с помощью SQL Server Data Tools](../run-a-package-in-sql-server-data-tools.md)  
  
-   [Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также  
 [Программа dtexec](dtexec-utility.md)   
 [мастер импорта и экспорта SQL Server](../import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)  
  
  
