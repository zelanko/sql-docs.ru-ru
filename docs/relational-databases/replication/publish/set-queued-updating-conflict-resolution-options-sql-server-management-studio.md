---
title: Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e0259cd61f563c50dbed0fdeac2cbebf11418b03
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850992"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>настроить параметры разрешения конфликтов обновления посредством очередей (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Установить параметры разрешения конфликтов для публикаций, которые поддерживают подписки, обновляемые посредством очередей, можно на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Установка параметров разрешения конфликтов обновления посредством очередей  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** выберите одно из следующих значений для параметра **Политика разрешения конфликтов**:  
  
    -   **Сохранить изменение издателя**  
  
    -   **Сохранить изменение подписчика**  
  
    -   **Повторно инициализировать подписку**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Включение обновляемых подписок для публикаций транзакций](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
