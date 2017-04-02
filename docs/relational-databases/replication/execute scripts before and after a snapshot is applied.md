---
title: "выполнять скрипты до и после применения моментального снимка (среда SQL Server Management Studio) | Microsoft Docs"
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
  - "моментальные снимки [репликация SQL Server], скрипты"
  - "скрипты [репликация SQL Server], моментальные снимки"
  - "репликация моментального снимка [SQL Server], скрипты"
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# выполнять скрипты до и после применения моментального снимка (среда SQL Server Management Studio)
  Указать пользовательский сценарий для выполнения до или после применения моментального снимка на **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Эти параметры будут недоступны при **Формат моментального снимка** включен режим **символ**.  
  
### Выполнение скрипта до или после применения моментального снимка  
  
1.  На **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно:  
  
    -   Чтобы указать скрипт для выполнения до применения моментального снимка, щелкните **Обзор** для перехода к скрипту или введите путь к скрипту в текстовом поле **Перед применением моментального снимка выполнить этот скрипт** .  
  
        > [!NOTE]  
        >  У агента распространителя или агента слияния должны быть разрешения на чтение в указанном каталоге. Если используются подписки по запросу, необходимо указать общий каталог как универсальных имен пути (UNC), например \\\computername\scripts\myscript.sql.  
  
    -   Чтобы указать скрипт для выполнения после применения моментального снимка, щелкните **Обзор** для перехода к скрипту или введите путь к скрипту в текстовом поле **После применения моментального снимка выполнить этот скрипт** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## См. также:  
 [Настроить свойства моментального снимка & #40; Программирование репликации Transact-SQL и #41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Выполнение скриптов до и после применения моментального снимка](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  