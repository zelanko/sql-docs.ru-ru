---
title: "Безопасность агента чтения журнала (одноранговая репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
f1_keywords:
- sql13.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b064576c5edd65059bdfcf2950fc4482da8e41d5
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>Безопасность агента чтения журнала (одноранговая репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  На странице **Безопасность агента чтения журнала** можно указать учетные записи, под которыми агент чтения журнала запускается и устанавливает соединения на каждом узле. Сведения о разрешениях, требуемых агентами, и об оптимальных методах защиты репликации см. в статьях [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md) и [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Для каждой базы данных, опубликованной с использованием репликации транзакций, существует по одному агенту чтения журнала. Если агент чтения журнала для базы данных уже настроен (либо для публикации при предыдущем запуске этого мастера, либо для другой публикации транзакций в этой же базе данных), то нельзя изменить учетные данные, которые он использует, в этом мастере. При указании новых учетных данных они будут проигнорированы. Учетные данные можно изменить в диалоговом окне **Свойства публикации** . Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Параметры  
 Нажмите кнопку свойств (**...**) в строке каждого узла, чтобы открыть диалоговое окно **Безопасность агента чтения журнала** . Нажмите кнопку **Справка** в открывшемся окне **Безопасность агента чтения журнала** , чтобы получить дополнительные сведения о разрешениях доступа, необходимых учетным записям, используемым агентами.  
  
 После ввода параметров в диалоговом окне, в сетке отображаются сведения о соединении для подписчика.  
  
 **Агенты для издателя**  
 Имя каждого экземпляра узла в одноранговой сети.  
  
 **Одноранговая база данных**  
 База данных каждого узла одноранговой сети, которая служит базой данных публикации и базой данных подписки.  
  
 **Соединение с распространителем**  
 Контекст, в котором устанавливается соединение с распространителем. Локальное соединение с распространителем всегда устанавливается в контексте учетной записи Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)], под которой запущен агент; таким образом, в этом поле всегда будет отображаться следующее: **Impersonate '\<домен>\\<имя_для_входа\>'** или **Impersonate '\<компьютер>\\<имя_для_входа\>'**.  
  
 **Соединение с издателем**  
 Контекст, в котором осуществляется соединение с издателем. Устанавливать соединение с издателем можно при помощи имени входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в контексте учетной записи Windows, под которой запущен агент. В поле отображается одна из следующих строк: **Use login '\<Имя_для_входа>'**, **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выполнять соединение в контексте учетной записи Windows.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
