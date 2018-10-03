---
title: Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 09c7f65a83ca1ec3190a87f4191fd01ed80f9231
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196284"
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
  
  
