---
title: "указать местоположение альтернативной папки моментальных снимков (среда SQL Server Management Studio) | Microsoft Docs"
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
  - "моментальные снимки [репликация SQL Server], альтернативные расположения папок"
  - "репликация моментального снимка [SQL Server], альтернативные расположения папок"
  - "альтернативные папки моментальных снимков [репликация SQL Server]"
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# указать местоположение альтернативной папки моментальных снимков (среда SQL Server Management Studio)
  Укажите другое расположение моментальных снимков на **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Указание альтернативной папки моментальных снимков  
  
1.  На **моментального снимка** Страница **Свойства публикации — \< публикация>** диалоговое окно:  
  
    1.  Выберите **Поместить файлы в следующую папку**, затем нажмите кнопку **Обзор** , чтобы перейти в каталог, или введите путь к каталогу, в который должны сохраняться файлы моментальных снимков.  
  
        > [!NOTE]  
        >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать общий каталог как универсальных имен пути (UNC), например \\\computername\snapshot. Дополнительные сведения см. в разделе [Безопасность папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
    2.  Снимите флажок **Поместить файлы в папку по умолчанию** , если не требуется, чтобы файлы были помещены в оба расположения.  
  
     Для сжатия файлов моментальных снимков выберите **Сжать файлы моментальных снимков в этом расположении**. Сжатие обычно используется для узкополосных подключений и для альтернативных расположений моментальных снимков на сменных носителях, таких, как компакт-диски.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## См. также:  
 [Альтернативные местоположения папки моментальных снимков](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Настроить свойства моментального снимка & #40; Программирование репликации Transact-SQL и #41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Укажите местоположение моментальных снимков по умолчанию & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  