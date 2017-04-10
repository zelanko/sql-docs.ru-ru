---
title: "Клиентские протоколы — свойства именованных каналов (вкладка &#171;Протокол&#187;) | Microsoft Docs"
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
  - "каналы [SQL Server], подключение"
  - "Именованные каналы [SQL Server], канал по умолчанию"
  - "клиентские протоколы [SQL Server]"
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Клиентские протоколы — свойства именованных каналов (вкладка &#171;Протокол&#187;)
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** диалогового окна **Свойства именованных каналов** для просмотра или изменения описания канала по умолчанию. Для подключения к другому каналу введите название канала в поле **Канал по умолчанию** . Дополнительные сведения о строках соединения см. в разделе [Creating a Valid Connection String Using Named Pipes](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md).  
  
## Параметры  
 **Канал по умолчанию**  
 Задает канал по умолчанию, который будет использоваться сетевой библиотекой именованных каналов для попыток подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query`  
  
 Чтобы подключиться к каналу по умолчанию, введите `sql\query`  
  
 **Включено**  
 Возможные значения: **Да** и **Нет**.  
  
## См. также  
 [Выбор сетевого протокола](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  