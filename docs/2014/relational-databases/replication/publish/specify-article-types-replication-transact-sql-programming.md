---
title: Определение типов статей (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- stored procedures [SQL Server replication], publishing
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bcd980bb7fe77e2d207e568802dfd7e69e9a1484
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882120"
---
# <a name="specify-article-types-replication-transact-sql-programming"></a>задать типы статей (программирование репликации на языке Transact-SQL)
  При репликации по умолчанию статьи имеют тип статей таблиц, но может производиться публикация и других типов объектов базы данных — представлений, хранимых процедур, определяемых пользователем функций и результатов выполнения хранимых процедур. Задать тип статьи программным путем при ее создании можно при помощи хранимых процедур репликации. Какие именно хранимые процедуры для этого применяются, зависит от типа репликации и типа статьи.  
  
> [!NOTE]  
>  Если при определении статьи таблицы, представления или хранимой процедуры указана только схема, то производится репликация только определения объекта.  
  
### <a name="to-publish-a-table-article-in-a-transactional-or-snapshot-publication"></a>Публикация статьи таблицы в публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. Укажите одно из следующих значений для ** \@типа** , чтобы определить тип статьи:  
  
    -   **logbased** — статья таблицы на основе журнала, которая используется по умолчанию для репликации транзакций и моментальных снимков. Репликация автоматически создает хранимую процедуру, применяемую для горизонтальной фильтрации, и представление, определяющее статью с вертикальной фильтрацией.  
  
    -   **logbased manualfilter** — статья на основе журнала с горизонтальной фильтрацией, где хранимая процедура, используемая для горизонтальной фильтрации, создается и определяется пользователем вручную и задается для ** \@фильтра**. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
    -   **logbased manualview** — статья на основе журнала с вертикальной фильтрацией, в которой представление, определяющее вертикально фильтруемую статью, создается и определяется пользователем и задается для ** \@sync_object**. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
    -   **logbased manualboth** — статья на основе журнала, горизонтальная и вертикально фильтруемая, где как хранимая процедура, используемая для горизонтальной фильтрации, так и представление, определяющее вертикально отфильтрованную статью, создаются и определяются пользователем и задаются соответственно для ** \@фильтров** и ** \@sync_object**. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
2.  Выполните процедуру **sp_articlefilter** для статей **logbased manualboth** и [logbased manualfilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) , чтобы создать хранимую процедуру фильтрации для статьи с горизонтальной фильтрацией. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
3.  Выполните процедуру **sp_articleview**для статей **logbased manualboth**, **logbased manualview** и [logbased manualfilter](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) , чтобы создать представление, определяющее статью с вертикальной фильтрацией. Дополнительные сведения см. в разделе [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-view-or-indexed-view-article-in-a-transactional-or-snapshot-publication"></a>Публикация статьи представления или индексированного представления в публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. Укажите одно из следующих значений для ** \@типа** , чтобы определить тип статьи:  
  
    -   **индексированное представление logbased** — статья индексированного представления, основанная на журнале. Репликация автоматически создает хранимую процедуру, применяемую для горизонтальной фильтрации, и представление, определяющее статью с вертикальной фильтрацией.  
  
    -   **Просмотр только схемы** — статья с представлением только схемы. Также необходимо выполнить репликацию базовой таблицы.  
  
    -   **только схема индексированного представления** — статья индексированного представления только для схемы. Также необходимо выполнить репликацию базовой таблицы.  
  
    -   **индексированное представление logbased manualfilter** — статья индексированного представления по горизонтали с горизонтальной фильтрацией, где хранимая процедура, используемая для горизонтальной фильтрации, создается и определяется пользователем вручную и задается для ** \@фильтра**. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
    -   **индексированное представление logbased manualview** — статья с отфильтрованным индексированным представлением на основе журнала, в которой представление, определяющее вертикально фильтруемую статью, создается и определяется пользователем и задается для ** \@sync_object**. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
    -   **индексированное представление logbased manualboth** — статья с отфильтрованным индексированным представлением на основе журнала, где хранимая процедура, используемая для горизонтальной фильтрации, и представление, определяющее вертикально фильтруемую статью, создаются и определяются пользователем и задаются соответственно для ** \@фильтров** и ** \@sync_object**. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
2.  Выполните процедуру **sp_articlefilter** для статей **logbased manualboth** и [logbased manualfilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) , чтобы создать хранимую процедуру фильтрации для статьи с горизонтальной фильтрацией. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
3.  Выполните процедуру **sp_articleview**для статей **logbased manualboth**, **logbased manualview** и [logbased manualfilter](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) , чтобы создать представление, определяющее статью с вертикальной фильтрацией. Дополнительные сведения см. в разделе [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-stored-procedure-stored-procedure-execution-or-user-defined-function-article-in-a-transactional-or-snapshot-publication"></a>Публикация статьи хранимой процедуры, выполнение хранимой процедуры или определяемой пользователем функции в публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. Укажите одно из следующих значений для ** \@типа** , чтобы определить тип статьи:  
  
    -   **proc schema only** — статья хранимой процедуры только со схемой.  
  
    -   **proc exec** — реплицирует выполнение хранимой процедуры всем подписчикам статьи. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **Serializable proc exec** — реплицирует выполнение хранимой процедуры только в том случае, если она выполняется в контексте сериализуемой транзакции. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **func schema only** — статья определяемой пользователем функции, которая доступна только для схемы.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
### <a name="to-publish-a-table-or-view-article-in-a-merge-publication"></a>Публикация статьи таблицы или представления в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите одно из следующих значений для ** \@типа** , чтобы определить тип статьи:  
  
    -   **Таблица** — статья таблицы.  
  
    -   **только схема индексированного представления** — статья индексированного представления только для схемы.  
  
    -   **Просмотр только схемы** — статья с представлением только схемы.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
### <a name="to-publish-a-stored-procedure-or-user-defined-function-article-in-a-merge-publication"></a>Публикация статьи хранимой процедуры или определяемой пользователем функции в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите одно из следующих значений для ** \@типа** , чтобы определить тип статьи:  
  
    -   **func schema only** — статья определяемой пользователем функции, которая доступна только для схемы.  
  
    -   **proc schema only** — статья хранимой процедуры только со схемой.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия системных хранимых процедур репликации](../concepts/replication-system-stored-procedures-concepts.md)   
 [Публикация данных и объектов базы данных](publish-data-and-database-objects.md)  
  
  
