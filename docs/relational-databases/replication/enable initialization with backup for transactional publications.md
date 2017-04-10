---
title: "включить инициализацию из резервной копии для публикаций транзакций (среда SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ручная инициализация подписки [репликация SQL Server]"
  - "подписки [репликация SQL Server], инициализация"
  - "инициализация подписок [репликация SQL Server], без моментальных снимков"
  - "репликация транзакций, резервное копирование и восстановление"
  - "резервные копии [репликация SQL Server], репликация транзакций"
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# включить инициализацию из резервной копии для публикаций транзакций (среда SQL Server Management Studio)
  Для инициализации подписки на публикацию транзакций из резервной копии сначала активизируйте публикацию, чтобы разрешить инициализацию из резервной копии, а затем, создавая подписку, укажите сведения о резервной копии:  
  
-   Активизируйте публикацию на **Параметры подписки** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Укажите сведения о резервной копии с помощью хранимой процедуры [sp_addsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Дополнительные сведения о параметрах **sp_addsubscription**, в разделе [Инициализация подписки на публикацию транзакций из резервной копии и #40; Программирование репликации Transact-SQL & #41;](../../relational-databases/replication/initialize a transactional subscription from a backup.md).  
  
### Включение инициализации с помощью резервной копии  
  
1.  На **Параметры подписки** Страница **Свойства публикации — \< публикация>** диалоговое окно, выберите значение **True** для **Разрешать инициализацию из файлов резервных копий** параметр.  
  
## См. также:  
 [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  