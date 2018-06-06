---
title: Подписчики репликации и группы доступности AlwaysOn (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ae868a9446b7cc140b6af61362358bb784488b9
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34769010"
---
# <a name="replication-subscribers-and-always-on-availability-groups-sql-server"></a>Подписчики репликации и группы доступности AlwaysOn (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Если в группе доступности AlwaysOn, содержащей базу данных, которая является подписчиком репликации, выполняется отработка отказа, то подписка на репликацию может завершиться ошибкой. Для подписчиков транзакций агент распространителя сможет продолжить репликацию автоматически, если в подписке используется имя прослушивателя группы доступности подписчика. Для подписчиков на публикацию слиянием администратор репликации должен вручную перенастроить подписчик путем повторного создания подписки.  
  
## <a name="what-is-supported"></a>Что поддерживается  
 Репликация [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает автоматический переход на другой ресурс для издателя и подписчиков транзакций. Отработка отказа распространителя на базе данных доступности не поддерживается. Подписчики на публикацию слиянием могут входить в группу доступности, но после отработки отказа потребуется вручную настроить нового подписчика. Группы доступности нельзя объединять со сценариями Websync и ssNoVersion Compact.  
  
## <a name="how-to-create-transactional-subscription-in-an-always-on-environment"></a>Создание подписок транзакций в среде AlwaysOn  
 Для настройки и отработки отказа группы доступности подписчика в отношении репликации транзакций выполните следующие действия.  
  
1.  Прежде чем создавать подписку, добавьте базу данных подписчика в соответствующую группу доступности AlwaysOn.  
  
2.  Добавьте прослушиватель группы доступности подписчика в качестве связанного сервера во все узлы группы доступности. Это действие гарантирует, что все возможные участники отработки отказа будут знать о существовании прослушивателя и смогут к нему подключиться.  
  
3.  Используя сценарий в **Создание Репликации Транзакции Принудительной Подписки** разделе ниже, создайте подписку, используя имя прослушивателя группы доступности подписчика. После отработки отказа имя прослушивателя всегда будет допустимым, а фактическое имя сервера подписчика будет зависеть от того, какой узел стал основным.  
  
    > [!NOTE]  
    >  Подписка должна быть создана с использованием сценария [!INCLUDE[tsql](../../../includes/tsql-md.md)] и не может быть создана с использованием [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
4.  Создание подписки по запросу.  
  
    1.  В среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]на основном узле подписчика откройте дерево агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    2.  Найдите задание **агента распространителя по запросу** и измените его.  
  
    3.  На шаге задания **Запуск агента** выполните проверку параметров `-Publisher` и `-Distributor` . Эти параметры должны содержать правильные имена непосредственно применяемого сервера, экземпляра издателя и распространителя.  
  
    4.  В качестве значения параметра `-Subscriber` укажите имя прослушивателя группы доступности подписчика.  
  
 Когда подписка создается с помощью этих действий, вам не придется больше ничего делать после отработки отказа.  
  
## <a name="creating-a-transactional-replication-push-subscription"></a>Создание Репликации Транзакции Принудительной Подписки  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a>Возобновление работы агентов слияния после переноса группы доступности подписчика  
 Для репликации слиянием администратор репликации должен вручную перенастроить подписчик следующим образом.  
  
1.  Выполните процедуру **sp_subscription_cleanup** , чтобы удалить старую подписку для подписчика. Запустите действие на новой первичной реплике (которая раньше была вторичной репликой).  
  
2.  Создайте подписку заново, начиная с нового моментального снимка.  
  
> [!NOTE]  
>  Текущий процесс неудобен для подписчиков репликации слиянием, однако основным сценарием для репликации слиянием являются отключенные пользователи (ПК, ноутбуки, переносные устройства), которые не используют группы доступности AlwaysOn в подписчике.  
  
  
