---
title: "Диспетчер HTTP-соединений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4cf63461848933530a215a75b19d40128327f356
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="http-connection-manager"></a>диспетчер HTTP-соединений
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
  
## <a name="configuration-of-the-http-connection-manager"></a>Настройка диспетчера HTTP-соединений  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
-   [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)  
  
 Дополнительные сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.  
  
## <a name="see-also"></a>См. также  
 [Задача «Веб-служба»](../../integration-services/control-flow/web-service-task.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
