---
title: Запуск системного монитора | Документация Майкрософт
description: Системный монитор использует удаленные вызовы процедур для сбора данных из SQL Server. Любой пользователь, обладающий разрешениями для запуска системного монитора, может отслеживать работу SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: ee6fb05d0ec83fe38acbef4ad80494c3a4a5c975
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505968"
---
# <a name="run-system-monitor"></a>Запуск системного монитора
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Системный монитор использует удаленные вызовы процедур (RPC) для сбора данных о Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Любой пользователь, обладающий разрешениями Microsoft Windows для запуска системного монитора, может его для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  При использовании системного монитора нельзя подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному в системе Windows 98.  
  
 Как и в случаях со всеми средствами мониторинга производительности, следует ожидать некоторого снижения производительности при использовании системного монитора для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Реальное снижение производительности на каком-либо определенном экземпляре зависит от аппаратного обеспечения, числа счетчиков и выбранного интервала обновления. Однако системный монитор специально интегрирован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для уменьшения снижения производительности.  
  
> [!NOTE]  
>  Если для мониторинга выбраны счетчики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в системном мониторе, то счетчики будут видны, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не работает.  
  
 Сведения о запуске системного монитора см. в разделе [Запуск системного монитора (Windows)](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  
