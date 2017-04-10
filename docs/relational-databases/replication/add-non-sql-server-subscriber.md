---
title: "Добавить подписчик, отличный от подписчика SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.addnonsqlsubscriber.f1"
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Добавить подписчик, отличный от подписчика SQL Server
  Репликация поддерживает принудительные подписки на моментальные снимки и публикации транзакций для подписчиков Oracle и IBM DB2.  
  
## Параметры  
 **Тип добавляемого подписчика:**  
 Выберите подписчик Oracle или подписчик IBM DB2. Дополнительные сведения об этих подписчиках см. в разделе [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Имя источника данных**  
 Данное имя позволяет найти базу данных в сети. Строка соединения с базой данных, формируемая репликацией, содержит имя источника данных, имя входа, пароль и параметры соединения, указанные на странице **Безопасность агента распространителя** данного мастера.  
  
> [!NOTE]  
>  Строка подключения и имя источника данных не проверяются [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пока агент распространителя пытается инициализировать подписку.  
  
## См. также:  
 [Создание подписки для подписчика, отличного от подписчика SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Подписчики, отличные от подписчиков SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  