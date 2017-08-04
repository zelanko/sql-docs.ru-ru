---
title: "Диспетчер FTP-соединений | Документы Microsoft"
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
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 04cc47e64fbbaec3f1e1df9216ead850efa75b90
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="ftp-connection-manager"></a>диспетчер FTP-соединений
  Диспетчер FTP-соединений позволяет пакету подключаться к серверу, использующему протокол передачи файлов (FTP). Задача «FTP», включенная в комплект служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений.  
  
 При добавлении к пакету диспетчера подключений FTP [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который может быть разрешен в соединение FTP во время выполнения, устанавливает свойства диспетчера подключений и добавляет его к коллекции **Подключения** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **FTP**.  
  
 Диспетчер FTP-сеансов может быть настроен следующим образом.  
  
-   Укажите имя и порт сервера.  
  
-   Выберите анонимный доступ или укажите имя пользователя и пароль для обычной проверки подлинности.  
  
    > [!IMPORTANT]  
    >  Диспетчер FTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
-   Задайте время ожидания, число повторных попыток и количество данных, которое будет копироваться за один раз.  
  
-   Укажите, должен ли диспетчер FTP-сеансов использовать пассивный или активный режим.  
  
 В зависимости от настройки сайта FTP, к которому подключается диспетчер FTP-сеансов, может понадобиться изменить следующие значения по умолчанию для диспетчера подключений.  
  
-   Для сервера порта устанавливается значение 21. Необходимо задать порт для прослушивания FTP-сайтом.  
  
-   Имя пользователя установлено в значение «anonymous». Необходимо предоставить учетные данные, которые требует веб-сайт FTP.  
  
## <a name="activepassive-modes"></a>Активный/пассивный режимы  
 Диспетчер FTP-соединений может отправлять и получать данные либо в активном, либо в пассивном режиме. В активном режиме подключение к данным инициируется сервером, а в пассивном режиме — клиентом.  
  
## <a name="configuration-of-the-ftp-connection-manager"></a>Настройка диспетчера FTP-соединений  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера FTP-сеансов](../../integration-services/connection-manager/ftp-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Задача «FTP»](../../integration-services/control-flow/ftp-task.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
