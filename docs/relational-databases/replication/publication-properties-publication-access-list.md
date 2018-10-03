---
title: Свойства публикации, страница "Список доступа к публикации" | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8dfe6ea6cace81776deefe3b0824d7289e9ed6b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784502"
---
# <a name="publication-properties-publication-access-list"></a>Свойства публикаций, список доступа к публикации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Страница **Список доступа публикации** в диалоговом окне **Свойства публикации** , позволяет добавлять имена входа, учетные записи и группы в список доступа к публикации и удалять их из него. Список доступа к публикации представляет собой первичный механизм защиты издателя. При создании публикации репликация создает список доступа для этой публикации. Список доступа к публикации, функционирующий также, как и список управления доступом в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, содержит список имен входа, учетных записей и групп, которым предоставлен доступ к публикации.  
  
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
  
  
