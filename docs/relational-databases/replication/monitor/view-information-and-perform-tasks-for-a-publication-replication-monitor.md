---
title: Просмотр сведений и выполнение задач для публикации (монитор репликации) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing publication information
- publications [SQL Server replication], viewing information
- publications [SQL Server replication], Replication Monitor tasks
ms.assetid: 92e28a07-d6a7-461b-a0b3-bd9bc6afcbe5
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fbe11687aefa08102d1b8a74534b53d31f561fe8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32958259"
---
# <a name="view-information-and-perform-tasks-for-a-publication-replication-monitor"></a>Просмотр сведений и выполнение задач для публикации (монитор репликации)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор репликации содержит следующие вкладки, предоставляющие информацию о выбранной публикации:  
  
-   **Все подписки**  
  
     На этой вкладке отображаются сведения о всех подписках на выбранную публикацию.  
  
-   **Агенты**  
  
     На этой вкладке отображаются сведения о всех агентах, используемых в публикации.  
  
    -   Агент моментальных снимков, используемый всеми публикациями.  
  
    -   Агент чтения журналов, используемый всеми публикациями транзакций.  
  
    -   Агент чтения очереди, используемый публикациями транзакций, имеющих обновляемые посредством очередей подписки.  
  
-   **Предупреждения** (для распространителей, на которых выполняется [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздние версии)  
  
    -   Эта вкладка позволяет задать предупреждения для агентов.  
  
-   **Трассировочные токены** (только для репликации транзакций, для распространителей, использующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более позднюю версию).  
  
     Эта вкладка позволяет измерять величину задержки между моментом фиксации транзакции на издателе и моментом фиксации соответствующей транзакции на подписчике.  
  
 Чтобы перейти к дополнительным сведениям о параметрах на каждой вкладке, щелкните вкладку на правой панели, а затем нажмите **Справка** в строке меню. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-a-publication"></a>Просмотр информации и выполнение задач публикации  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Для просмотра и изменения свойств публикации щелкните публикацию правой кнопкой мыши, затем щелкните **Свойства**.  
  
3.  Для просмотра сведений о подписках щелкните вкладку **Все подписки** .  
  
     Для просмотра и изменения свойств подписки щелкните подписку правой кнопкой мыши, затем щелкните **Свойства**. На этой вкладке можно также просмотреть другие подробные сведения и выполнить дополнительные задачи. Дополнительные сведения см. в статье [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
4.  Чтобы просмотреть сведения об агентах, перейдите на вкладку **Агенты** . На этой вкладке можно также просмотреть другие подробные сведения и выполнить дополнительные задачи. Дополнительные сведения см. в статье [Просмотр сведений и выполнение задач для агентов, связанных с публикацией (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
5.  Чтобы просмотреть сведения о предупреждениях агентов и пороговых значениях, перейдите на вкладку **Предупреждения** . Дополнительные сведения см. в разделе [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
6.  Чтобы просмотреть сведения о трассировочных токенах, перейдите на вкладку **Трассировочные токены** . Дополнительные сведения об использовании трассировочных токенов см. в разделе [Измерение задержки и проверка правильности соединений для репликации транзакций](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
