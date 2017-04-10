---
title: "задать типы статей (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "публикация [репликация SQL Server], выполнения хранимой процедуры"
  - "статьи [репликация SQL Server], параметры репликации транзакций"
  - "статьи [репликация SQL Server], параметры репликации слиянием"
  - "хранимые процедуры [репликация SQL Server], публикация"
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# задать типы статей (программирование репликации на языке Transact-SQL)
  При репликации по умолчанию статьи имеют тип статей таблиц, но может производиться публикация и других типов объектов базы данных — представлений, хранимых процедур, определяемых пользователем функций и результатов выполнения хранимых процедур. Задать тип статьи программным путем при ее создании можно при помощи хранимых процедур репликации. Какие именно хранимые процедуры для этого применяются, зависит от типа репликации и типа статьи.  
  
> [!NOTE]  
>  Если при определении статьи таблицы, представления или хранимой процедуры указана только схема, то производится репликация только определения объекта.  
  
### Публикация статьи таблицы в публикации моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра **@type** .  
  
    -   **logbased** -статьи таблицы на основе журнала, которая используется по умолчанию для репликации транзакций или моментальных снимков. Репликация автоматически создает хранимую процедуру, применяемую для горизонтальной фильтрации, и представление, определяющее статью с вертикальной фильтрацией.  
  
    -   **logbased manualfilter** -статья на основе журнала, горизонтально фильтруемой где хранимая процедура, используемая для горизонтальной фильтрации вручную создается и определяется пользователем и для **@filter**. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **logbased manualview** -статья на основе журнала, отфильтрованный по вертикали где представление, определяющее статью с вертикальной фильтрацией создается и определяется пользователем и для **@sync_object**. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **logbased manualboth** -на основе журнала, горизонтально и вертикально фильтруемой статьи, где создаются и определенных пользователем хранимая процедура, используемая для горизонтальной фильтрации и представление, определяющее статью с вертикальной фильтрацией и указанные для **@filter** и **@sync_object**, соответственно. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Для **logbased manualboth** и **logbased manualfilter** статей, [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) Чтобы создать хранимую процедуру фильтрации для статьи с горизонтальной фильтрацией. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Для **logbased manualboth**, **logbased manualview**, и **logbased manualfilter** статей, [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) для создания представления, определяющего вертикально фильтруемой статьи. Дополнительные сведения см. в статье [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### Публикация статьи представления или индексированного представления в публикации моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра **@type** .  
  
    -   **индексированные представления logbased** -статья на основе журнала индексированного представления. Репликация автоматически создает хранимую процедуру, применяемую для горизонтальной фильтрации, и представление, определяющее статью с вертикальной фильтрацией.  
  
    -   **только схема представления** -статьи только для схемы представления. Также необходимо выполнить репликацию базовой таблицы.  
  
    -   **только схема индексированного представления** -статьи только для схемы индексированного представления. Также необходимо выполнить репликацию базовой таблицы.  
  
    -   **индексированные представления logbased manualfilter** -статья на основе журнала, горизонтально фильтруемой индексированного представления, где хранимая процедура, используемая для горизонтальной фильтрации вручную создается и определяется пользователем и для **@filter**. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **индексированные представления logbased manualview** -статья на основе журнала, отфильтрованные индексированного представления, где представление, определяющее статьи с вертикальным фильтром создается и определяется пользователем и для **@sync_object**. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **индексированные представления logbased manualboth** -статья на основе журнала, отфильтрованные индексированного представления, где хранимая процедура, используемая для горизонтальной фильтрации и представление, определяющее статьи с вертикальным фильтром создаются и определенных пользователем и для **@filter** и **@sync_object**, соответственно. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Для **logbased manualboth** и **logbased manualfilter** статей, [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) Чтобы создать хранимую процедуру фильтрации для статьи с горизонтальной фильтрацией. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Для **logbased manualboth**, **logbased manualview**, и **logbased manualfilter** статей, [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) для создания представления, определяющего вертикально фильтруемой статьи. Дополнительные сведения см. в статье [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### Публикация статьи хранимой процедуры, выполнение хранимой процедуры или определяемой пользователем функции в публикации моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра **@type** .  
  
    -   **только схема proc** -статьи только для схемы хранимой процедуры.  
  
    -   **proc exec** -реплицирует выполнение хранимой процедуры всем подписчикам на статью. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **Serializable proc exec** -реплицирует выполнение хранимой процедуры только в том случае, если она выполняется в контексте сериализуемой транзакции. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **только схема Func** -статьи только для схемы определяемой пользователем функции.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
### Публикация статьи таблицы или представления в публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра **@type** .  
  
    -   **Таблица** -статьи таблицы.  
  
    -   **только схема индексированного представления** -статьи только для схемы индексированного представления.  
  
    -   **только схема представления** -статьи только для схемы представления.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
### Публикация статьи хранимой процедуры или определяемой пользователем функции в публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра **@type** .  
  
    -   **только схема Func** -статьи только для схемы определяемой пользователем функции.  
  
    -   **только схема proc** -статьи только для схемы хранимой процедуры.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## См. также:  
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  