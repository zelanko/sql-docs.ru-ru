---
title: "Свойства публикации, страница \"Список доступа к публикации\" | Документация Майкрософт"
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
f1_keywords: sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8fc6fe8d96844640d6a6723209e60086096d25b4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="publication-properties-publication-access-list"></a>Свойства публикаций, список доступа к публикации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Страница **Список доступа к публикации** в диалоговом окне **Свойства публикации** позволяет добавлять имена входа, учетные записи и группы в список доступа к публикации и удалять их из него. Список доступа к публикации представляет собой первичный механизм защиты издателя. При создании публикации репликация создает список доступа для этой публикации. Список доступа к публикации, функционирующий также, как и список управления доступом в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, содержит список имен входа, учетных записей и групп, которым предоставлен доступ к публикации.  
  
 Когда подписчик подключается к издателю или распространителю и запрашивает доступ к публикации, имя входа подписчика сопоставляется со сведениями проверки подлинности в списке доступа к публикации. Это обеспечивает дополнительную безопасность издателя, так как имена входа издателя и распространителя не могут использоваться клиентскими средствами для внесения изменений непосредственно на издателе. Дополнительные сведения см. в статье [Организация безопасности издателя](../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="options"></a>Параметры  
 **Добавить**  
 Добавить в список новую запись. Можно добавить только те имена входа, учетные записи или группы, которые уже определены и на издателе, и на распространителе. Они определяются на обоих серверах, если используются учетные записи домена или были созданы локальные учетные записи на обоих серверах.  
  
 **Удалить**  
 Удалить выбранную запись из списка.  
  
 **Удалить все**  
 Удалить все записи из списка.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
