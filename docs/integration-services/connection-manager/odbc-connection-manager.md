---
title: "Диспетчер соединений ODBC | Microsoft Docs"
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
  - "соединения [службы Integration Services], ODBC"
  - "диспетчер соединений ODBC"
  - "источники данных [службы Integration Services], подключения"
  - "диспетчеры подключений [службы Integration Services], ODBC"
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# Диспетчер соединений ODBC
  Диспетчер соединений ODBC позволяет пакету подключаться к разнообразным системам управления базами данных, используя открытый интерфейс взаимодействия с базами данных (ODBC).  
  
 При добавлении соединения ODBC к пакету и задании свойств диспетчера соединений службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений и добавляют его к коллекции **Connections** пакета. Во время выполнения диспетчер соединений рассматривается как физическое соединение с ODBC.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **ODBC**.  
  
 Настроить диспетчер соединений ODBC можно следующими способами:  
  
-   Предоставить строку соединения, которая ссылается на пользовательское или системное имя источника данных.  
  
-   Указать сервер, к которому нужно подключиться.  
  
-   Указать, сохранять ли соединение во время выполнения.  
  
## Настройка диспетчера соединений ODBC  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Справочник по пользовательскому интерфейсу диспетчера соединений ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## См. также  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  