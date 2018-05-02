---
title: Учебники по репликации | Документация Майкрософт
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3900aae4e96b5490b0b65cbbee004fc66337ff63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="replication-tutorials"></a>Учебники по репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Технология репликации обеспечивает эффективный перенос данных или подмножеств данных между серверами. Репликация транзакций применяется для репликации данных между полностью подключенными серверами. Также можно выполнять репликацию данных между серверами и клиентами, между которыми отсутствует постоянное подключение, посредством репликации слиянием. Ниже приводятся учебники, которые помогут вам подготовить сервер для репликации, а также содержат сведения о настройке репликации транзакций и репликации слиянием. 
  
В учебниках по репликации "Издатель" означает сервер, который содержит реплицируемые данные источника, а "Подписчик" — целевой сервер. Издатель и подписчик могут совместно использовать один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это не является обязательным. Дополнительные сведения см. в разделе [Обзор модели публикации репликации](../../relational-databases/replication/publish/replication-publishing-model-overview.md).  

В рамках этих учебников сервер NODE1\SQL2016 выступает в качестве издателя и распространителя, а сервер NODE2\SQL2016 — в качестве подписчика. 
  
> [!NOTE]  
> Большинство задач, представленных в этих учебниках, могут выполняться программным способом. Дополнительные сведения см. в разделе [Документация для разработчика репликации](../../relational-databases/replication/concepts/replication-developer-documentation.md).  
  
## <a name="replication-tutorials"></a>Учебники по репликации  
[Учебник. Подготовка SQL Server для репликации — издатель, распространитель, подписчик](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md) 
 
Изучите как подготавливать серверы, чтобы репликация могла быть выполнена с минимумом прав доступа. Прежде чем перейти к другим учебникам по репликации, необходимо закончить выполнение данного учебника.  
  
[Учебник. Настройка репликации между двумя полностью подключенными серверами (репликация транзакций)](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)

Изучите, как настраивать репликацию транзакций для репликации данных между полностью подключенными серверами. В этом учебнике также описываются основные методы устранения неполадок. 

  
[Учебник. Настройка репликации между сервером и мобильными клиентами (репликация слиянием)](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)

Изучите, как настраивать репликацию слиянием для обмена данными между сервером и одним или более клиентами, которые подключаются периодически.  
  
## <a name="see-also"></a>См. также:  
[Безопасность и защита при репликации](../../relational-databases/replication/security/security-and-protection-replication.md) 

[Обзор репликации транзакций](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication) 

[Обзор репликации слиянием](https://docs.microsoft.com/en-us/sql/relational-databases/replication/merge/merge-replication)

  