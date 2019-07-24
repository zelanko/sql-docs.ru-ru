---
title: Параметр конфигурации сервера "affinity64 Input-Output mask" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a0f63af10e8baf21cf17d316f64e66d4e663852
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68013180"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a>Параметр конфигурации сервера "affinity64 Input-Output mask"
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **affinity64 I/O mask** , подобно параметру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinity I/O mask **, привязывает операции ввода-вывода сервера** к заданному подмножеству процессоров. Параметр **affinity I/O mask** используется для привязки первых 32 процессоров, оставшиеся процессоры компьютера привязываются при помощи параметра **affinity64 I/O mask** . После изменения параметра **affinity64 I/O mask**необходимо перезапустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр доступен только в 64-разрядной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера "affinity Input-Output mask"](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  
