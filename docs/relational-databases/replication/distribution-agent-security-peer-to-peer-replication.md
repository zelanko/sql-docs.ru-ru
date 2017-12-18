---
title: "Безопасность агента распространителя (одноранговая репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2719c816be19a18f3042e9bcd2e9e8d139f5d84
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a>Безопасность агента распространителя (одноранговая репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На странице **Безопасность агента распространителя** можно указать учетные записи, с которыми агент распространения будет выполняться и устанавливать соединения с компьютерами в одноранговой топологии. Сведения о разрешениях, требуемых агентами, и об оптимальных методах защиты репликации см. в статьях [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md) и [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Если агент распространителя для подписки уже был настроен во время предыдущего запуска мастера, в этом мастере нельзя изменить используемые агентом учетные данные. При указании новых учетных данных они будут проигнорированы. Чтобы изменить учетные данные, используйте диалоговое окно **Свойства подписки** . Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Параметры  
 Чтобы открыть диалоговое окно**Безопасность агента распространителя**, в строке для каждого подписчика нажмите кнопку свойств ( **...** ). Чтобы получить дополнительные сведения о разрешениях, необходимых для учетных записей, используемых агентами, нажмите кнопку **Справка** в открывшемся диалоговом окне **Безопасность агента распространителя** .  
  
 После ввода параметров в одном из диалоговых окон в сетке будут отображены сведения о соединении для подписчика.  
  
 **Агент для подписчика**  
 Имя каждого узла одноранговой сети.  
  
 **Одноранговая база данных**  
 База данных узла одноранговой сети, которая будет служить одновременно базой данных публикации и подписки.  
  
 **Соединение с распространителем**  
 Контекст, в котором устанавливается соединение с распространителем. Локальные соединения всегда осуществляются с использованием контекста учетной записи Windows, с которой запущен агент. Мастер создает принудительные подписки (у которых локальным соединением является соединение с распространителем), поэтому в этом поле всегда будет отображаться следующее: **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'**.  
  
 **Соединение с подписчиком**  
 Контекст, в котором устанавливается соединение с подписчиком. Соединение может устанавливаться в контексте учетной записи Windows, с которой работает агент, либо в контексте имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В поле отображается одна из следующих строк: **Use login '\<Имя_для_входа>'**, **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выполнять соединение в контексте учетной записи Windows.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
