---
title: "Зеркальное отображение базы данных: взаимодействие и сосуществование (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5e35b0184fd4a6d22a0feaf2373050b964eb3d86
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Зеркальное отображение базы данных: взаимодействие и сосуществание (SQL Server)
  Зеркальное отображение базы данных можно использовать со следующими возможностями и компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [Экземпляры отказоустойчивой кластеризации AlwaysOn (отказоустойчивый кластер SQL Server)](../../database-engine/database-mirroring/database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Отслеживание измененных данных (и отслеживание изменений)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Моментальные снимки базы данных](../../database-engine/database-mirroring/database-mirroring-and-database-snapshots-sql-server.md)  
  
-   [Полнотекстовые каталоги](../../database-engine/database-mirroring/database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [доставка журналов;](../../database-engine/database-mirroring/database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Репликация](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)  
  
 Зеркальное отображение базы данных не работает совместно со следующими функциями.  
  
-   Транзакции между разными базами данных или распределенные транзакции  
  
     Сведения о том, почему не поддерживаются такие транзакции, см. в разделе [Транзакции между базами данных и распределенные транзакции для групп доступности AlwaysOn и зеркального отображения базы данных (SQL Server)](../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  

