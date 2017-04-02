---
title: "Свойства публикации, агент безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.agentsecurity.f1"
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Свойства публикации, агент безопасности
  Страница **Безопасность агентов** диалогового окна **Свойства публикации** позволяет получить доступ к параметрам учетных записей, от имени которых запускаются и соединяются с компьютерами в топологии репликации следующие агенты.  
  
-   Агент моментальных снимков для всех публикаций.  
  
-   Агент чтения журнала для всех публикаций транзакций. У каждой базы данных, опубликованной для репликации транзакций, может быть только один агент чтения журнала. Изменение настроек агента чтения журнала затрагивает все публикации транзакций в базе данных.  
  
-   Агент чтения очереди для публикаций транзакций, допускающих подписки, обновляемые посредством очередей. Для каждой базы распространителя существует только один агент чтения очереди. Изменение агента чтения очереди затрагивает все публикации транзакций с обновляемыми посредством очередей подписками, использующими одну и ту же базу данных распространителя. Дополнительные сведения об агенте чтения очереди см. в разделе [Просмотр и изменение настроек безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Дополнительные сведения о настройках безопасности и разрешениях, необходимых для каждого агента, см. в разделе [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Параметры  
 **Параметры безопасности** или **Создать агент**  
 Если задание агента был создан, нажмите кнопку **Параметры безопасности** чтобы открыть диалоговое окно для изменения настроек безопасности для агента. Если задание агента не было создано, щелкните **Создать агент** , чтобы создать его и задать настройки безопасности.  
  
## См. также:  
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Безопасность и защита и #40; Репликация & #41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  