---
title: "Запуск системного монитора | Microsoft Docs"
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
  - "системный монитор [SQL Server], выполнение"
  - "системный монитор Windows [SQL Server], выполнение"
  - "вызовы удаленных процедур [SQL Server]"
  - "запуск системного монитора Windows NT"
  - "RPC"
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Запуск системного монитора
  Системный монитор использует удаленные вызовы процедур (RPC) для сбора данных о Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Любой пользователь, обладающий разрешениями Microsoft Windows для запуска системного монитора, может его для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  При использовании системного монитора нельзя подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенному в системе Windows 98.  
  
 Как и в случаях со всеми средствами мониторинга производительности, следует ожидать некоторого снижения производительности при использовании системного монитора для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Реальное снижение производительности на каком-либо определенном экземпляре зависит от аппаратного обеспечения, числа счетчиков и выбранного интервала обновления. Однако системный монитор специально интегрирован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для уменьшения снижения производительности.  
  
> [!NOTE]  
>  Если для мониторинга выбраны счетчики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в системном мониторе, то счетчики будут видны, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не работает.  
  
 Сведения о запуске системного монитора см. в разделе [Запуск системного монитора (Windows)](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  