---
title: "MSSQL_ENG021385 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG021385, ошибка"
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG021385
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21385|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удалось создать моментальный снимок для публикации "%s". Возможно, из-за изменений в схеме или из-за статей, добавленных во время создания снимка.|  
  
## Объяснение  
 Данная ошибка возникает, если агент моментальных снимков начинает работу во время выполняющихся изменений в базе данных публикации, включающих добавление или удаление статей и внесение изменений схемы в опубликованные объекты.  
  
## Действие пользователя  
 После завершения изменений в базе данных публикации перезапустите агент моментальных снимков. Дополнительные сведения см. в разделе [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  