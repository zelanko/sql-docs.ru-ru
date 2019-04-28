---
title: Параметр конфигурации сервера "affinity64 Input-Output mask" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f32c35aabf7d95a31624ca5c507fccac8ba1053e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62811571"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a>Параметр конфигурации сервера "affinity64 Input-Output mask"
  Параметр **affinity64 I/O mask** , подобно параметру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinity I/O mask **, привязывает операции ввода-вывода сервера** к заданному подмножеству процессоров. Параметр **affinity I/O mask** используется для привязки первых 32 процессоров, оставшиеся процессоры компьютера привязываются при помощи параметра **affinity64 I/O mask** . После изменения параметра **affinity64 I/O mask**необходимо перезапустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр доступен только в 64-разрядной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Параметр конфигурации сервера "affinity Input-Output mask"](affinity-input-output-mask-server-configuration-option.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
