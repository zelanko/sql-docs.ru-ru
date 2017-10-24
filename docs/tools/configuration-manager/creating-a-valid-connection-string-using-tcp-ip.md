---
title: "Создание допустимой строки соединения с использованием протокола TCP/IP | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8611848c01d854e373e3e945e9d7c6d69df0c2ce
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a>Создание допустимой строки подключения с использованием протокола TCP/IP
  Чтобы создать допустимую строку подключения с использованием протокола TCP/IP, выполните следующие действия.  
  
-   Укажите **Имя псевдонима**.  
  
-   В поле **Сервер**введите имя сервера, к которому можно подключиться с помощью команды **PING** , или IP-адрес, к которому можно подключиться с помощью команды **PING** . Для именованного экземпляра добавьте имя экземпляра.  
  
-   Укажите **TCP/IP** в поле **Протокол**.  
  
-   При необходимости в поле **Номер порта**введите номер порта. Номер порта по умолчанию равен 1433. Это номер порта экземпляра по умолчанию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на сервере. Для подключения к именованному экземпляру или к экземпляру по умолчанию, не прослушивающему порт 1433, необходимо указать номер порта или запустить службу « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , браузер». Дополнительные сведения о настройке службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Служба браузера SQL Server](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 Во время соединения компонент собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] считывает значения сервера, протокола и порта из реестра для заданного имени псевдонима и создает строку подключения в формате `tcp:<servername>[\<instancename>],<port>` или `tcp:<IPAddress>[\<instancename>],<port>`.  
  
> [!NOTE]  
>  Брандмауэр Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)] по умолчанию закрывает порт 1433. Поскольку [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обменивается данными через порт 1433, необходимо повторно открыть порт Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на прослушивание клиентских соединений при помощи протокола TCP/IP. Информацию о настройке брандмауэра см. в статье "Настройка брандмауэра Windows для разрешения доступа к SQL Server" в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или документации по вашей версии брандмауэра.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client полностью поддерживают протокол IP версии 4 (IPv4) и протокол IP версии 6 (IPv6). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager принимает IPv4 и IPv6 форматы для IP-адресов. Сведения о протоколе IPv6 см. в разделе "Подключение при помощи IPv6" электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="connecting-to-the-local-server"></a>Подключение к локальному серверу  
 При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполняющемуся на том же компьютере, что и клиент, в качестве имени сервера можно использовать `(local)` . Это действие не рекомендуется, поскольку может вызвать неоднозначность, но может быть полезным, если известно, что клиент запущен на нужном компьютере. Например, при создании приложения для мобильных отключенных пользователей, таких как торговый персонал, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запускаться на переносных компьютерах и использоваться для хранения данных проекта, клиент, подключающийся к `(local)` , всегда будет подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполняющемуся на переносном компьютере. Слово `localhost` или точку (**.**) можно использовать вместо `(local)`.  
  
## <a name="verifying-your-connection-protocol"></a>Проверка протокола соединения  
 Следующий запрос возвращает протокол, используемый в текущем соединении.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Примеры  
 Подключение по имени сервера:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Подключение по имени сервера к именованному экземпляру:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 Подключение по имени сервера к указанному порту:  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Подключение по IP-адресу:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Подключение по IP-адресу к именованному экземпляру:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 Подключение по IP-адресу к указанному порту:  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Подключение к локальному компьютеру при помощи `(local)`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 Подключение к локальному компьютеру при помощи `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 Подключение к именованному экземпляру на локальном компьютере `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 Соединение с локальным компьютером при помощи точки:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 Соединение с именованным экземпляром на локальном компьютере при помощи точки:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  Сведения о настройке сетевого протокола с помощью параметра **sqlcmd** см. в статье "Подключение к компоненту Database Engine при помощи программы sqlcmd" в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Создание допустимой строки соединения с использованием именованных каналов](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [Выбор сетевого протокола](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  

