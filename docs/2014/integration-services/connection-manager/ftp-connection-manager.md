---
title: Диспетчер FTP-соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 989049c5371d35d53282f5780dcfc9db13312c7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188844"
---
# <a name="ftp-connection-manager"></a>диспетчер FTP-соединений
  Диспетчер FTP-соединений позволяет пакету подключаться к серверу, использующему протокол передачи файлов (FTP). Задача «FTP», включенная в комплект служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений.  
  
 При добавлении в пакет диспетчера FTP-сеансов службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, обеспечивающий соединение с FTP во время выполнения, устанавливают свойства диспетчера соединений и добавляют диспетчер соединений в коллекцию `Connections` данного пакета.  
  
 `ConnectionManagerType` Свойства диспетчера соединений присваивается `FTP`.  
  
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
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера FTP-сеансов](../ftp-connection-manager-editor.md).  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Задача "FTP"](../control-flow/ftp-task.md)   
 [Службы Integration Services &#40;SSIS&#41; подключений](integration-services-ssis-connections.md)  
  
  
