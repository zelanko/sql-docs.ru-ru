---
title: "Просмотр и остановка пакетов, выполняющихся на сервере служб Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты [службы Integration Services], управление"
  - "управление выполняющимися пакетами [службы Integration Services]"
  - "пакеты [службы Integration Services], выполняемые"
  - "выполняемый пакет [службы Integration Services], управление"
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Просмотр и остановка пакетов, выполняющихся на сервере служб Integration Services
  В базе данных служб **SSISDB** хранится журнал выполнения во внутренних таблицах, невидимых для пользователей. Однако сведения, которые она предоставляет, можно получить с помощью запросов к общим представлениям. Также она предоставляет хранимые процедуры, которые можно вызвать для выполнения стандартных задач, связанных с пакетами.  
  
 Обычно управление объектами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сервере выполняется в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Но также можно создать запросы к представлениям базы данных и вызывать хранимые процедуры напрямую, либо написать специальный код, вызывающий управляемый API-интерфейс. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и управляемый API-интерфейс для выполнения многих задач отправляют запросы к представлениям и вызывают хранимые процедуры. Например, можно просмотреть список пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выполняющихся в данный момент на сервере, и запросить остановку их выполнения при необходимости.  
  
## Просмотр списка выполняемых пакетов  
 Можно просмотреть список пакетов, которые в данный момент выполняются на сервере, в диалоговом окне **Активные операции** . Дополнительные сведения см. в статье [Active Operations Dialog Box](../../integration-services/performance/active-operations-dialog-box.md).  
  
 Дополнительные сведения о других методах, которые можно использовать для просмотра списка запущенных пакетов, см. в следующих разделах.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] доступ  
 Чтобы просмотреть список пакетов, запущенных на сервере, создайте запрос к представлению [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md) для пакетов со значением состояния 2.  
  
 Программный доступ с использованием управляемого API-интерфейса  
 См. пространство имен <xref:Microsoft.SqlServer.Management.IntegrationServices> и его классы.  
  
## Остановка выполнения пакета  
 Можно запросить остановку выполняющегося пакета в диалоговом окне **Активные операции** . Дополнительные сведения см. в статье [Active Operations Dialog Box](../../integration-services/performance/active-operations-dialog-box.md).  
  
 Дополнительные сведения о других методах, которые можно использовать для остановки запущенного пакета, см. в следующих разделах.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] доступ  
 Чтобы остановить выполняемый на сервере пакет, следует вызвать хранимую процедуру [catalog.stop_operation (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md).  
  
 Программный доступ с использованием управляемого API-интерфейса  
 См. пространство имен <xref:Microsoft.SqlServer.Management.IntegrationServices> и его классы.  
  
## Просмотр журнала выполненных пакетов  
 Для просмотра журнала пакетов, выполнявшихся в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], используйте отчет **Все выполнения** . Дополнительные сведения об отчете **Все выполнения** и других стандартных отчетах см. в разделе [Отчеты для сервера служб Integration Services](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
 Сведения о других методах, которые можно использовать для просмотра журнала выполняющихся пакетов, см. в следующих разделах.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] доступ  
 Для просмотра сведений о выполнявшихся пакетах запросите представление [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md).  
  
 Программный доступ с использованием управляемого API-интерфейса  
 См. пространство имен <xref:Microsoft.SqlServer.Management.IntegrationServices> и его классы.  
  
## См. также  
 [Запуск проектов и пакетов](https://msdn.microsoft.com/library/hh213290.aspx)   
 [Устранение неполадок пакетов с помощью отчетов](https://msdn.microsoft.com/library/gg471512.aspx)  
  
  