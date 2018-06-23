---
title: Параметр конфигурации сервера "affinity64 mask" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processor affinity [SQL Server]
- affinity64 mask option
- binding processors [SQL Server]
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d141ea3bba60e20b8a29c69369744d86397c72a2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101822"
---
# <a name="affinity64-mask-server-configuration-option"></a>Параметр конфигурации сервера «affinity64 mask»
  Параметр affinity64 mask привязывает процессоры к конкретным потокам, аналогично параметру affinity mask. Используйте параметр affinity mask для привязки первых 32-разрядных процессоров и параметр affinity64 mask для привязки оставшихся процессоров на компьютере. Этот параметр доступен только в 64-разрядной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] Используйте вместо него инструкцию [ALTER SERVER CONFIGURATION (Transact-SQL)](/sql/t-sql/statements/alter-server-configuration-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Параметр конфигурации сервера «affinity mask»](affinity-mask-server-configuration-option.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
