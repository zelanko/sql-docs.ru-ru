---
title: "Диспетчер HTTP-соединений | Microsoft Docs"
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
  - "диспетчер HTTP-соединений"
  - "соединения с веб-сайтом [службы Integration Services]"
  - "диспетчеры подключений [службы Integration Services], HTTP"
  - "соединения с веб-сервером [службы Integration Services]"
  - "подключения [службы Integration Services], HTTP"
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
caps.latest.revision: 44
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# Диспетчер HTTP-соединений
  HTTP-соединение позволяет пакету получить доступ к веб-серверу через протокол HTTP, чтобы передавать или принимать файлы. Задача «Веб-служба» из состава служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует этот диспетчер соединений.  
  
 При добавлении к пакету диспетчера HTTP-соединений [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который будет решать задачи HTTP-соединений во время работы, устанавливает свойства диспетчера соединений и добавляет его к коллекции **Connections** пакета.  
  
 Свойство диспетчера соединений **ConnectionManagerType** имеет значение **HTTP.**  
  
 Произвести настройку диспетчера HTTP-соединений можно следующими способами:  
  
-   Используйте учетные данные. Если диспетчер соединений использует учетные данные, то необходимо указать имя пользователя, пароль и домен.  
  
    > [!IMPORTANT]  
    >  Диспетчер HTTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
-   Используйте сертификат клиента. Если диспетчер соединений использует сертификат клиента, то среди его свойств есть имя сертификата.  
  
-   Введите время ожидания при подключении к серверу и размер фрагмента данных для записи данных.  
  
-   Используйте прокси-сервер. Прокси-сервер также может быть настроен для использования учетных данных, а также для обхода прокси-сервера и использования локальных адресов.  
  
## Настройка диспетчера HTTP-соединений  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
-   [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)  
  
 Дополнительные сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.  
  
## См. также  
 [Задача «Веб-служба»](../../integration-services/control-flow/web-service-task.md)   
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  