---
title: "Диспетчер соединений SQL Server Compact Edition | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Compact, диспетчер подключений"
  - "подключения [службы Integration Services], SQL Server Compact"
  - "диспетчеры подключений [службы Integration Services], SQL Server Compact"
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Диспетчер соединений SQL Server Compact Edition
  Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact позволяет пакету подключаться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Целевое назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, содержащееся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений для загрузки данных в таблицы базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  На 64-разрядном компьютере пакеты, которые соединяются с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, должны запускаться в 32-разрядном режиме. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, используемый службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для соединения с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, доступен только в 32-разрядной версии.  
  
## Настройка диспетчера соединений SQL Server Compact Edition  
 Когда диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact добавляется к пакету, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений для разрешения соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact во время выполнения, задают свойства диспетчера соединений и добавляют его к коллекции **Connections** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **SQLMOBILE**.  
  
 Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact можно настроить следующими способами:  
  
-   указать строку соединения, в которой задается расположение базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact;  
  
-   указать пароль для защищенной паролем базы данных;  
  
-   указать сервер, на котором хранится база данных;  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  