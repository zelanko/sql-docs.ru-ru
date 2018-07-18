---
title: Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf77195076c4467babaa85c19202449b567367ef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37262430"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>настроить параметры разрешения конфликтов обновления посредством очередей (среда SQL Server Management Studio)
  Установить параметры разрешения конфликтов для публикаций, которые поддерживают подписки, обновляемые посредством очередей, можно на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Установка параметров разрешения конфликтов обновления посредством очередей  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** выберите одно из следующих значений для параметра **Политика разрешения конфликтов**:  
  
    -   **Сохранить изменение издателя**  
  
    -   **Сохранить изменение подписчика**  
  
    -   **Повторно инициализировать подписку**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Включение обновляемых подписок для публикаций транзакций](enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
