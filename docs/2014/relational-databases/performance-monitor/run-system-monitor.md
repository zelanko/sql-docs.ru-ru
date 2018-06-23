---
title: Запуск системного монитора | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 53e6fa6b09523bd03e4fbad8e9ae40248e738c78
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095651"
---
# <a name="run-system-monitor"></a>Запуск системного монитора
  Системный монитор использует удаленные вызовы процедур (RPC) для сбора данных о Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Любой пользователь, обладающий разрешениями Microsoft Windows для запуска системного монитора, может его для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  При использовании системного монитора нельзя подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному в системе Windows 98.  
  
 Как и в случаях со всеми средствами мониторинга производительности, следует ожидать некоторого снижения производительности при использовании системного монитора для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Реальное снижение производительности на каком-либо определенном экземпляре зависит от аппаратного обеспечения, числа счетчиков и выбранного интервала обновления. Однако системный монитор специально интегрирован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для уменьшения снижения производительности.  
  
> [!NOTE]  
>  Если для мониторинга выбраны счетчики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в системном мониторе, то счетчики будут видны, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не работает.  
  
 Сведения о запуске системного монитора см. в разделе [Запуск системного монитора (Windows)](../performance/start-system-monitor-windows.md).  
  
  