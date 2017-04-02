---
title: "Параметр конфигурации сервера &#171;remote admin connections&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "соединения администратора [SQL Server]"
  - "DAC"
  - "подключения [SQL Server], выделенный администратор"
  - "remote admin connections, параметр"
  - "выделенные административные соединения [SQL Server]"
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Параметр конфигурации сервера &#171;remote admin connections&#187;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет выделенное административное соединение (DAC). Такое подключение позволяет администратору получать доступ к серверу для выполнения диагностических функций или инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или решения проблем на сервере, даже когда сервер заблокирован или работает в аварийном состоянии и не отвечает на соединение компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. По умолчанию выделенные административные соединения доступны только с клиента на сервер. Чтобы разрешить клиентским приложениям на удаленных компьютерах подключение DAC, используйте параметр remote admin connections хранимой процедуры sp_configure.  
  
 По умолчанию DAC ожидает соединения только на IP-адресе обратной связи (127.0.0.1), порт 1434. Если TCP-порт 1434 недоступен, то TCP-порт динамически назначается при запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Если на компьютере установлено более одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо проверить номер TCP-порта в журнале ошибок.  
  
 В следующей таблице приведены возможные значения параметра remote admin connections.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Означает, что разрешены только локальные соединения через DAC.|  
|1|Означает, что разрешены удаленные соединения через DAC.|  
  
## Пример  
 В следующем примере показано подключение через DAC с удаленного компьютера.  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## См. также:  
 [Диагностическое соединение для администраторов баз данных](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
  