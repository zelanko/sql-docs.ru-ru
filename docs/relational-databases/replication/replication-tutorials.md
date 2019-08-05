---
title: Учебники по репликации | Документы Майкрософт
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 6a99d15ba812edac0408262ba1ae26d7ea8b8dbc
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768440"
---
# <a name="replication-tutorials"></a>Учебники по репликации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
Технология репликации обеспечивает эффективный перенос данных или подмножеств данных между серверами. Репликация транзакций применяется для репликации данных между полностью подключенными серверами. Также можно использовать репликацию для данных между серверами и клиентами, между которыми отсутствует постоянное подключение, посредством репликации слиянием. В этой статье приводятся учебники, которые помогут вам подготовить сервер к репликации, а также сведения о настройке репликации транзакций и репликации слиянием. 
  
В учебниках по репликации "Издатель" — это сервер, который содержит реплицируемые данные источника. "Подписчик" — это целевой сервер. Издатель и подписчик могут совместно использовать один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это необязательно. Дополнительные сведения см. в разделе [Обзор модели публикации репликации](../../relational-databases/replication/publish/replication-publishing-model-overview.md).  

В этих учебниках сервер NODE1\SQL2016 выступает в качестве издателя и распространителя. Сервер NODE2\SQL2016 выступает в качестве подписчика. 
  
> [!NOTE]  
> Большинство задач, представленных в этих учебниках, могут выполняться программным способом. Дополнительные сведения см. в разделе [Документация для разработчика репликации](../../relational-databases/replication/concepts/replication-developer-documentation.md).  
  
## <a name="replication-tutorials"></a>Учебники по репликации  
[Учебник. Подготовка SQL Server к репликации (издатель, распространитель, подписчик)](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md) 
 
Изучите как подготавливать серверы, чтобы репликация могла быть выполнена с минимумом прав доступа. Прежде чем перейти к другим учебникам по репликации, необходимо закончить выполнение данного учебника.  
  
[Учебник. Настройка репликации между двумя полностью подключенными серверами (репликация транзакций)](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)

Вы узнаете, как настраивать репликацию транзакций для репликации данных между полностью подключенными серверами. В этом учебнике также описываются основные методы устранения неполадок. 

  
[Учебник. Настройка репликации между сервером и мобильными клиентами (репликация слиянием)](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)

Вы узнаете, как настраивать репликацию слиянием для обмена данными между сервером и одним клиентом, который подключается периодически, или несколькими.  
  
## <a name="see-also"></a>См. также раздел  
[Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md) 

[Обзор репликации транзакций](https://docs.microsoft.com/sql/relational-databases/replication/transactional/transactional-replication) 

[Обзор репликации слиянием](https://docs.microsoft.com/sql/relational-databases/replication/merge/merge-replication)

  
