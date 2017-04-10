---
title: "MSSQL_REPL027056 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027056, ошибка"
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027056
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|27056|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Процессу слияния не удалось изменить журнал поколений в '%1'. В целях диагностики запустите синхронизацию повторно, включив подробное протоколирование и укажите выходной файл для записи.|  
  
## Объяснение  
 Эта ошибка обычно возникает в результате состязания между чрезмерно увеличившимися системными таблицами репликации слиянием. Большой размер системных таблицы обычно обусловлен длительным сроком хранения публикации, поскольку метаданные должны сохраняться в этих таблицах до тех пор, пока не закончится срок хранения.  
  
## Действие пользователя  
 **Способы устранения проблемы.**  
  
1.  Уменьшить значение**DownloadGenerationsPerBatch** и **- UploadGenerationsPerBatch** продолжать выполнение, пока будут устраняться основные параметры для агента слияния разрешить обработку выдачи вызывает ошибку. Параметры агента могут задаваться в профилях агента или в командной строке. Дополнительные сведения см. в разделе:  
  
    -   [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Просмотр и изменение параметров командной строки агента репликации & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
2.  Укажите наименьшее возможное значение срока хранения публикации. Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
3.  Как часть обслуживания репликации слиянием, проверяйте время рост системных таблиц, связанных с репликацией слиянием: **MSmerge_contents**, **MSmerge_genhistory**, и **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, и **MSmerge_past_partition_mappings**. Время от времени проводите повторную индексацию этих таблиц. Дополнительные сведения см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  