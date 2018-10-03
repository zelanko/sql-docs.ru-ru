---
title: Диспетчер HTTP-соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8b0552d4678df69620d4e97f6f4e1a942dd12330
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113094"
---
# <a name="http-connection-manager"></a>диспетчер HTTP-соединений
  HTTP-соединение позволяет пакету получить доступ к веб-серверу через протокол HTTP, чтобы передавать или принимать файлы. Задача «Веб-служба» из состава служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует этот диспетчер соединений.  
  
 При добавлении к пакету диспетчера HTTP-соединений [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который будет решать задачи HTTP-соединений во время работы, устанавливают свойства диспетчера соединений и добавляют его к коллекции пакета `Connections`.  
  
 `ConnectionManagerType` Имеет значение свойства диспетчера соединений `HTTP.`  
  
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
  
-   [Редактор диспетчера HTTP-соединений &#40;страница сервера&#41;](../http-connection-manager-editor-server-page.md)  
  
-   [Редактор диспетчера HTTP-соединений &#40;страницы прокси-сервера&#41;](../http-connection-manager-editor-proxy-page.md)  
  
 Дополнительные сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.  
  
## <a name="see-also"></a>См. также  
 [Задача веб-службы](../control-flow/web-service-task.md)   
 [Службы Integration Services &#40;SSIS&#41; подключений](integration-services-ssis-connections.md)  
  
  
