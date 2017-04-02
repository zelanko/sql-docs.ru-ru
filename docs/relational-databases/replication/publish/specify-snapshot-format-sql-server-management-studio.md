---
title: "указать формат моментальных снимков (среда SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "моментальные снимки [репликация SQL Server], форматы"
  - "репликация моментального снимка [SQL Server], форматы"
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# указать формат моментальных снимков (среда SQL Server Management Studio)
  Укажите формат моментальных снимков на **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Указание формата моментальных снимков  
  
1.  На **моментального снимка** Страница **Свойства публикации — \< публикация>** выберите **собственный SQL Server — все подписчики должны быть серверами SQL Server** или **Символьный — необходим, если на издателе или подписчике не используется SQL Server**.  
  
    > [!NOTE]  
    >  Рекомендуется выбирать собственный формат всегда, кроме тех случаев, когда публикация должна поддерживать подписки на базу данных [!INCLUDE[ssEW](../../../includes/ssew-md.md)] или базу данных, отличную от базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## См. также:  
 [Настроить свойства моментального снимка & #40; Программирование репликации Transact-SQL и #41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  