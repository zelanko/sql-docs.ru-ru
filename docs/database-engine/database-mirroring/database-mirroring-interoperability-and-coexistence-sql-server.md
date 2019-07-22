---
title: Зеркальное отображение базы данных. Взаимодействие и сосуществование (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2d116624ddea37922e401244c3c669db0a81aa03
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006415"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Зеркальное отображение базы данных. Взаимодействие и сосуществование (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
