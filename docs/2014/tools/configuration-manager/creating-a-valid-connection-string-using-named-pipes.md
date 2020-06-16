---
title: Создание допустимой строки подключения с использованием именованных каналов | Документация Майкрософт
description: Узнайте, как создать допустимую строку подключения при использовании протокола именованных каналов для подключения к экземпляру SQL Server. Просмотр примеров допустимых имен каналов.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 65fcebc3bbe12061e699106fb23eed15a5498414
ms.sourcegitcommit: c8e45e0fdab8ea2ae1c7e709346354576b18ca1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716711"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>Создание допустимой строки соединения, использующей протокол именованных каналов
  Если пользователь по умолчанию [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает протокол именованных каналов, он использует в `\\.\pipe\sql\query` качестве имени канала. Точка означает, что компьютер является локальным компьютером, `pipe` указывает, что соединение является именованным каналом, а `sql\query` — именем канала. Чтобы подключиться к каналу по умолчанию, псевдоним должен содержать `\\<computer_name>\pipe\sql\query` в качестве имени канала. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был настроен на прослушивание другого канала, то имя канала должно соответствовать этому каналу. Например, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует в качестве канала `\\.\pipe\unit\app`, то псевдоним должен использовать `\\<computer_name>\pipe\unit\app` в качестве имени канала.  
  
 Создание допустимого имени канала  
  
-   Укажите **Имя псевдонима**.  
  
-   Выберите **именованные каналы** в качестве **протокола**.  
  
-   Введите **имя канала**. Кроме того, можно оставить **имя канала** пустым, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после того как вы укажете **протокол** и **сервер** , Configuration Manager заполнит соответствующее имя канала.  
  
-   Укажите **сервер**. Для именованного экземпляра можно ввести имя сервера и имя экземпляра.  
  
 Во время подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент собственного клиента считывает значения имени сервера, протокола и канала из реестра для указанного имени псевдонима и создает имя канала в формате `np:\\<computer_name>\pipe\<pipename>` или `np:\\<IPAddress>\pipe\<pipename>` . Для именованного экземпляра имя канала по умолчанию — `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query` .  
  
> [!NOTE]  
>  Брандмауэр Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)] по умолчанию закрывает порт 445. Так как [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляет связь через порт 445, необходимо повторно открыть порт, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для прослушивания клиентских подключений с помощью именованных каналов. Информацию о настройке брандмауэра см. в статье "Настройка брандмауэра Windows для разрешения доступа к SQL Server" в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или документации по вашей версии брандмауэра.  
  
## <a name="connecting-to-the-local-server"></a>Подключение к локальному серверу  
 При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполняющемуся на том же компьютере, что и клиент, в качестве имени сервера можно использовать `(local)`. Применение `(local)` не рекомендуется, поскольку может вызвать неоднозначность, но может быть полезным, если известно, что клиент запущен на нужном компьютере. Например, при создании приложения для мобильных отключенных пользователей, таких как торговый персонал, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запускаться на переносных компьютерах и использоваться для хранения данных проекта, клиент, подключающийся к (local), будет всегда подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполняющемуся на переносном компьютере. Слово `localhost` или точку (.) можно использовать вместо `(local)`.  
  
## <a name="verifying-your-connection-protocol"></a>Проверка протокола соединения  
 Следующий запрос возвратит протокол, используемый в текущем соединении.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Примеры  
 Подключение по имени сервера к каналу по умолчанию:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Подключение по IP-адресу к каналу по умолчанию:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 Подключение по имени сервера к каналу, отличному от канала по умолчанию:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Подключение по имени сервера к именованному экземпляру:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Подключение к локальному компьютеру при помощи `localhost`:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 Соединение с локальным компьютером при помощи точки:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  Сведения об указании сетевого протокола в качестве параметра **sqlcmd** см. в разделе «как подключиться к ядро СУБД с помощью sqlcmd.exe» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="see-also"></a>См. также:  
 [Создание допустимой строки подключения с помощью протокола общей памяти](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Создание допустимой строки подключения с помощью IP-адреса TCP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
