---
title: Создание допустимой строки соединения с использованием именованных каналов | Документация Майкрософт
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
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 12d5cb30217a0580d4da101d614b4930cfd8184b
ms.sourcegitcommit: ca9b5cb6bccfdba4cdbe1697adf5c673b4713d6c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56407594"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>Создание допустимой строки соединения, использующей протокол именованных каналов
  Если не изменено пользователем, когда экземпляр по умолчанию [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает протоколы именованных каналов, он использует `\\.\pipe\sql\query` как имя канала. Точка означает, что компьютер является локальным компьютером, `pipe` указывает, что подключение является именованным каналом, а `sql\query` имя канала. Чтобы подключиться к каналу по умолчанию, псевдоним должен содержать `\\<computer_name>\pipe\sql\query` в качестве имени канала. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был настроен на прослушивание другого канала, то имя канала должно соответствовать этому каналу. Например, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует в качестве канала `\\.\pipe\unit\app`, то псевдоним должен использовать `\\<computer_name>\pipe\unit\app` в качестве имени канала.  
  
 Создание допустимого имени канала  
  
-   Укажите **Имя псевдонима**.  
  
-   Выберите **именованные каналы** как **протокола**.  
  
-   Введите **имя канала**. Кроме того, можно оставить **имя канала** пустым и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager завершит соответствующее имя канала, после того как вы укажете **протокола** и **сервера**  
  
-   Укажите **сервера**. Для именованного экземпляра можно ввести имя сервера и имя экземпляра.  
  
 Во время подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент собственного клиента считывает значения сервера, протокола и имени канала из реестра для заданного имени псевдонима и создает имя канала в формате `np:\\<computer_name>\pipe\<pipename>` или `np:\\<IPAddress>\pipe\<pipename>`. Для именованного экземпляра имя канала по умолчанию — `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.  
  
> [!NOTE]  
>  Брандмауэр Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)] по умолчанию закрывает порт 445. Так как [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляет связь через порт 445, необходимо повторно открыть порт, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для прослушивания клиентских подключений с помощью именованных каналов. Сведения о настройке брандмауэра см. в разделе «Как настроить брандмауэр для приложения SQL Server Access» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в документации используемого брандмауэра.  
  
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
>  Для указания сетевого протокола **sqlcmd** параметр, см. в разделе «как: соединиться с компонентом Database Engine при помощи программы sqlcmd.exe» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Создание допустимой строки соединения с использованием протокола общей памяти](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Создание допустимой строки подключения с использованием протокола TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
