---
title: "Разнородная репликация базы данных | Документация Майкрософт"
ms.custom: 
ms.date: 08/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de92a656e372ae79c8ac17037c301cff52d3e928
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="heterogeneous-database-replication"></a>разнородная репликация базы данных  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает следующие разнородные сценарии для репликации транзакций и репликации моментальных снимков.  
  
-   Публикация данных с подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на подписчики, отличные от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   Публикация данных в Oracle и из Oracle имеет следующие ограничения:  
  | |2016 или более ранние версии |2017 или более поздние версии |
  |-------|-------|--------|
  |Репликация из Oracle |Поддержка только Oracle 10g или более ранних версий |Поддержка только Oracle 10g или более ранних версий |
  |Репликация в Oracle |Версии до Oracle 12c |Не поддерживается |


 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a>Публикация данных из Oracle  
 Для публикации данных из Oracle можно использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , причем большинство функций и простота их использования такие же, как и в случае репликации моментальных снимков и репликации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Для этой функции требуется Oracle 10G или более ранней версии. Публикация данных из Oracle идеально подходит для следующих сценариев:  
  
|Сценарий|Description|  
|--------------|-----------------|  
|Развертывание приложений на платформе[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Ведите разработку с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при работе с данными, реплицируемыми из базы данных, отличной от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Серверы промежуточного хранения данных|Поддерживайте синхронизацию промежуточных баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с базой данных, отличной от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Переход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Протестируйте приложения в реальном времени совместно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при репликации изменений исходной системы. Переключение на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при успешном испытании миграции.|  
  
 Дополнительные сведения см. в статье [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a>Публикация данных на подписчиках, отличных от подписчиков SQL Server  
 Следующие базы данных, отличные от баз данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , поддерживаются в качестве подписчиков для публикации моментальных снимков и публикации транзакций.  
  
-   Oracle для всех платформ с поддержкой Oracle.  
  
-   IBM DB2 для AS400, MVS, Unix, Linux и Windows.  
  
 Дополнительные сведения см. в статье [Non-SQL Server Subscribers](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
  
