---
title: "Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: "34"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60b92cb933e8ef7bf5978c289e42f6d986d5c548
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>настроить параметры разрешения конфликтов обновления посредством очередей (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Установить параметры разрешения конфликтов для публикаций, которые поддерживают подписки, обновляемые посредством очередей, можно на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Установка параметров разрешения конфликтов обновления посредством очередей  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** выберите одно из следующих значений для параметра **Политика разрешения конфликтов**:  
  
    -   **Сохранить изменение издателя**  
  
    -   **Сохранить изменение подписчика**  
  
    -   **Повторно инициализировать подписку**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Включение обновляемых подписок для публикаций транзакций](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
