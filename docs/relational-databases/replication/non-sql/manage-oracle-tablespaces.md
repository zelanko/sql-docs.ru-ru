---
title: "Управление табличными пространствами Oracle | Microsoft Docs"
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
  - "публикация Oracle [репликация SQL Server], управление табличными пространствами"
  - "табличный пространств [репликация SQL Server]"
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Управление табличными пространствами Oracle
  Табличное пространство — это единица хранилища базы данных, примерно эквивалентный группе файлов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Табличные пространства предоставляют возможности хранения и управления объектами баз данных в рамках индивидуальных групп. Дополнительные сведения см. в документации Oracle.  
  
 При настройке таблицы как части публикации Oracle можно при желании указать, что существующее табличное пространство Oracle будет использоваться для хранения информации о ходе репликации. В противном случае табличным пространством для объектов репликации будет табличное пространство по умолчанию, связанное с административной пользовательской схемой репликации, которая была настроена при настройке издателя.  
  
 **Указание табличного пространства для таблицы регистрации статей**:  
  
-   Задайте табличное пространство в диалоговом окне **Свойства статьи** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Используйте [sp_changearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Для использования **sp_changearticle**, укажите следующее:  
  
    -   имя издателя Oracle в качестве параметра **@publisher**;  
  
    -   имя публикации Oracle в качестве параметра **@publication**;  
  
    -   имя статьи в качестве параметра **@article**;  
  
    -   значение tablespace для параметра **@property**;  
  
    -   имя табличного пространства для параметра **@value**.  
  
## См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Объекты, создаваемые на издателе Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  