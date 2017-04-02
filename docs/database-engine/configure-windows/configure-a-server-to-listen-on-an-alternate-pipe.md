---
title: "Настройка сервера для прослушивания альтернативного канала (диспетчер конфигурации SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "именованные каналы [SQL Server], настройка"
  - "прослушивание [SQL Server], каналы"
  - "каналы [SQL Server], альтернативные"
  - "альтернативные каналы [SQL Server]"
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Настройка сервера для прослушивания альтернативного канала (диспетчер конфигурации SQL Server)
  В этом разделе описан процесс настройки сервера на прослушивание другого канала в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. По умолчанию неименованный экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] прослушивает именованный канал \\\\.\pipe\sql\query. Именованные экземпляры компонентов [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и [!INCLUDE[ssEW](../../includes/ssew-md.md)] настроены на прослушивание других каналов.  
  
 Клиентское приложение можно подключить к конкретному именованному каналу тремя способами:  
  
-   запустив на сервере службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создав псевдоним клиента с указанием именованного канала;  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### Настройка именованного канала, используемого компонентом SQL Server Database Engine  
  
1.  В области консоли диспетчера конфигурации SQL Server разверните узел **Сетевая конфигурация SQL Server**, а затем — **Протоколы для** *\<имя экземпляра>*.  
  
2.  В области сведений щелкните правой кнопкой мыши **Именованные каналы** и выберите пункт **Свойства**.  
  
3.  На вкладке **Протоколы** в поле **Имя канала** укажите канал, который должен прослушиваться компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] , и нажмите кнопку **ОК**.  
  
4.  В области консоли выберите **Службы SQL Server**.  
  
5.  В области сведений щелкните правой кнопкой мыши **SQL Server (**\<имя экземпляра>\>**)**, а затем нажмите кнопку **Перезагрузка**, чтобы остановить и перезагрузить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает альтернативный канал, то подключить клиентское приложение к конкретному именованному каналу можно тремя способами:  
  
-   запустив на сервере службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создав псевдоним клиента с указанием именованного канала;  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
## См. также:  
 [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create or delete a server alias for use by a client.md)   
 [Сетевая конфигурация сервера](../../database-engine/configure-windows/server-network-configuration.md)  
  
  