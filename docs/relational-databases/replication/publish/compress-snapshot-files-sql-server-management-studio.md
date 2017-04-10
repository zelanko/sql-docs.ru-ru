---
title: "сжать файлы моментальных снимков (среда SQL Server Management Studio) | Microsoft Docs"
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
  - "моментальные снимки [репликация SQL Server], сжатые"
  - "репликация моментального снимка [SQL Server], сжатые моментальные снимки"
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# сжать файлы моментальных снимков (среда SQL Server Management Studio)
  Укажите, что файлы должны сжиматься в **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Сжатие файлов моментальных снимков  
  
1.  На **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно:  
  
    1.  Выберите **Поместить файлы в следующую папку**, затем нажмите кнопку **Обзор** , чтобы перейти в каталог, или введите путь к каталогу, в который должны сохраняться файлы моментальных снимков.  
  
        > [!NOTE]  
        >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать общий каталог как универсальных имен пути (UNC), например \\\computername\snapshot. Дополнительные сведения см. в разделе [Безопасность папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
    2.  Снимите флажок **Поместить файлы в папку по умолчанию** , если не требуется, чтобы файлы были помещены в оба расположения.  
  
        > [!NOTE]  
        >  Если данный флажок установлен, файлы, хранящиеся в папке по умолчанию, не сжимаются. Сжатые файлы можно хранить только в альтернативной папке, указанной на предыдущем шаге.  
  
2.  Выберите **Выполнять сжатие файлов моментальных снимков в этой папке**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## См. также:  
 [Настроить свойства моментального снимка & #40; Программирование репликации Transact-SQL и #41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Сжатые моментальные снимки](../../../relational-databases/replication/compressed-snapshots.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  