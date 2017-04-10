---
title: "Диспетчер соединений SMO | Microsoft Docs"
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
  - "подключения [службы Integration Services], SMO"
  - "SMO, диспетчер соединений"
  - "диспетчеры подключений [службы Integration Services], SMO"
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Диспетчер соединений SMO
  Диспетчер соединений SMO позволяет пакету подключиться к серверу SQL Management Object (SMO). Задачи пересылки, включенные в службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , используют диспетчер соединений SMO. Например, задача «Передача имен входа», пересылающая данные для входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использует диспетчер соединений SMO.  
  
 При добавлении к пакету диспетчера подключений SMO [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который будет разрешен в соединение SMO во время выполнения, устанавливает свойства диспетчера подключений и добавляет его к коллекции **Подключения** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **SMOServer**.  
  
 Можно настроить диспетчер соединений SMO следующим образом:  
  
-   Указать имя сервера, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Выберите режим проверки подлинности для соединения с сервером.  
  
## Настройка диспетчера соединений SMO  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], см. в статье [Редактор диспетчера соединений SMO](../../integration-services/connection-manager/smo-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## См. также  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  