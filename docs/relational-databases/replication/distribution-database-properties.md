---
title: Свойства базы данных распространителя | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2ec47bad429a79f1995461e7a73f06bdad735acd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="distribution-database-properties"></a>Свойства базы данных распространителя
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Свойства базы данных распространителя** позволяет просмотреть набор свойств и задать срок хранения транзакций и журналов для текущей базы данных.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя базы данных распространителя, по умолчанию 'distribution' (только для чтения).  
  
 **Местоположение файлов**  
 Расположение файла базы данных и файла журнала (только для чтения).  
  
 **Срок хранения транзакций**  
 Также называется сроком хранения распространения. Время, в течение которого транзакции сохраняются для репликации транзакций. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Срок хранения журнала**  
 Время, в течение которого метаданные журнала сохраняются для всех типов репликации.  
  
 **Безопасность агента чтения очереди**  
 Агент чтения очереди используется репликацией транзакций с подписками, обновляемыми посредством очередей. Агент чтения очереди создается автоматически при выборе пункта **Публикации транзакций с обновляемыми подписками** на странице **Тип публикации** мастера создания публикаций. Выберите **Настройки безопасности…** для изменения учетной записи, от имени которой этот агент запускается и подключается к распространителю.  
  
 Агент чтения очереди можно также создать, выбрав пункт **Создать агент чтения очереди** на данной странице (этот элемент отключается, если такой агент уже создан).  
  
 Дополнительные сведения о соединениях для агента чтения очереди указываются в двух местах:  
  
-   Агент подключается к издателю с учетными данными, указанными в диалоговом окне **Свойства издателя** , доступном со страницы **Издатели** диалогового окна **Свойства распространителя** .  
  
-   Агент подключается к подписчику с учетными данными, указанными для агента распространителя в мастере создания подписок.  
  
 Дополнительные сведения см. в статье  [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
