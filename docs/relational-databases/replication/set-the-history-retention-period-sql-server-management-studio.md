---
title: "настроить срок хранения журнала (среда SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "срок хранения журнала [репликация SQL Server]"
  - "срок хранения [репликация SQL Server]"
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# настроить срок хранения журнала (среда SQL Server Management Studio)
  Укажите срок хранения журнала на **Общие** Страница **Свойства базы данных распространителя — \< База_данных_распространителя>** диалоговое окно. Эта настройка управляет длительностью хранения журнала агента репликации. Эта страница доступна из **Общие** Страница **Свойства распространителя — \< распространитель>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [представления и свойств издателя и распространителя изменить](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### Указание срока хранения журнала  
  
1.  На **Общие** Страница **Свойства распространителя — \< распространитель>** диалогового окна нажмите кнопку с многоточием (**...**) для базы данных распространителя.  
  
2.  Введите значение в поле **Сохранять журнал производительности репликации не менее** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## См. также:  
 [Настройка распространителя](../../relational-databases/replication/configure-distribution.md)  
  
  