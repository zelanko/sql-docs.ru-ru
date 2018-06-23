---
title: 'Зеркальное отображение базы данных: взаимодействие и сосуществование (SQL Server) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ba2e5af89a4a9eabb420e0d75a8a90b4ef48540
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192507"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Зеркальное отображение базы данных: взаимодействие и сосуществание (SQL Server)
  Зеркальное отображение базы данных можно использовать со следующими возможностями и компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [Экземпляры AlwaysOn отказоустойчивого кластера (отказоустойчивой кластеризацией SQL Server)](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Отслеживание измененных данных (и отслеживание изменений)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Моментальные снимки базы данных](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [Полнотекстовые каталоги](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [доставка журналов;](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Репликация](database-mirroring-and-replication-sql-server.md)  
  
 Зеркальное отображение базы данных не работает совместно со следующими функциями.  
  
-   Транзакции между разными базами данных или распределенные транзакции  
  
     Сведения о том, почему не поддерживаются такие транзакции, см. в разделе [Транзакции между базами данных не поддерживаются при зеркальном отображении баз данных или в группах доступности AlwaysOn (SQL Server)](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring-sql-server.md)  
  
  