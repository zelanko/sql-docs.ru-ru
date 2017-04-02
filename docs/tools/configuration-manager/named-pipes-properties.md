---
title: "Свойства именованных каналов | Microsoft Docs"
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
  - "каналы [SQL Server]"
  - "прослушивание [SQL Server], каналы"
  - "каналы [SQL Server], прослушивание каналов"
  - "именованные каналы [SQL Server], прослушивание каналов"
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Свойства именованных каналов
  Используйте страницу **Протокол** в диалоговом окне **Свойства именованных каналов**, чтобы просмотреть или изменить именованный канал, который прослушивается [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], во время использования протокола именованных каналов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть перезапущен, чтобы включить протокол, отключить протокол или изменить именованный канал.  
  
## Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Имя канала**  
 Указывает именованный канал, который прослушивается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query` для экземпляра по умолчанию и `\\.\pipe\MSSQL$<instancename>\sql\query` для именованного экземпляра. Длина этого поля ограничена 2047 символами.  
  
## Создание альтернативного именованного канала  
 Чтобы изменить именованный канал, введите новое имя канала в поле **Имя канала** , а затем остановите и перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Так как **sql\query** хорошо известен в качестве именованного канала, используемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], изменение канала может помочь сократить риск проведения атак вредоносными программами.  
  
### Пример  
 Введите **\\\\.\pipe\unit\app**, чтобы прослушивать канал **unit\app**.  
  
 Введите **\\\\.\pipe\acct**, чтобы прослушивать канал **acct**.  
  
## См. также  
 [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Выбор сетевого протокола](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [Создание допустимой строки соединения, использующей протокол именованных каналов](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  