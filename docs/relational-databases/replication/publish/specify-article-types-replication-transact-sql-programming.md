---
title: Определение типов статей (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: fab59450a2403eadc080a5f246c0911b164eba3a
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71710810"
---
# <a name="specify-article-types-replication-transact-sql-programming"></a>задать типы статей (программирование репликации на языке Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При репликации по умолчанию статьи имеют тип статей таблиц, но может производиться публикация и других типов объектов базы данных — представлений, хранимых процедур, определяемых пользователем функций и результатов выполнения хранимых процедур. Задать тип статьи программным путем при ее создании можно при помощи хранимых процедур репликации. Какие именно хранимые процедуры для этого применяются, зависит от типа репликации и типа статьи.  
  
> [!NOTE]  
>  Если при определении статьи таблицы, представления или хранимой процедуры указана только схема, то производится репликация только определения объекта.  
  
### <a name="to-publish-a-table-article-in-a-transactional-or-snapshot-publication"></a>Публикация статьи таблицы в публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)на издателе в базе данных публикации. Чтобы определить тип статьи, укажите одно из следующих значений параметра `@type`:  
  
    -   `logbased` — журнальная статья таблицы (значение по умолчанию для репликации транзакций и моментальных снимков). Репликация автоматически создает хранимую процедуру, применяемую для горизонтальной фильтрации, и представление, определяющее статью с вертикальной фильтрацией.  
  
    -   `logbased manualfilter` — журнальная статья с горизонтальной фильтрацией, где хранимая процедура для горизонтальной фильтрации создается вручную и определяется пользователем в параметре `@filter`. Дополнительные сведения см. в разделе [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -  `logbased manualview` — журнальная статья с вертикальной фильтрацией, где определяющее ее представление создается вручную пользователем и определяется в параметре `@sync_object`. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   `logbased manualboth` — журнальная статья с горизонтальной и вертикальной фильтрацией, где хранимая процедура для горизонтальной фильтрации и представление, определяющее вертикальную фильтрацию, создаются пользователем вручную и указываются в параметрах `@filter` и `@sync_object`. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Выполните процедуру [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) для статей `logbased manualboth` и `logbased manualfilter`, чтобы создать хранимую процедуру фильтрации для статьи с горизонтальной фильтрацией. Дополнительные сведения см. в разделе [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Выполните процедуру [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) для статей `logbased manualboth`, `logbased manualview` и `logbased manualfilter`, чтобы создать представление, определяющее статью с вертикальной фильтрацией. Дополнительные сведения см. в разделе [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="to-publish-a-view-or-indexed-view-article-in-a-transactional-or-snapshot-publication"></a>Публикация статьи представления или индексированного представления в публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)на издателе в базе данных публикации. Чтобы определить тип статьи, укажите одно из следующих значений параметра `@type`:  
  
    -   **indexed view logbased** — журнальная статья индексированного представления. Репликация автоматически создает хранимую процедуру, применяемую для горизонтальной фильтрации, и представление, определяющее статью с вертикальной фильтрацией.  
  
    -   **view schema only** — статья со схемой, соответствующая представлению. Также необходимо выполнить репликацию базовой таблицы.  
  
    -   **indexed view schema only** — статья со схемой, соответствующая индексированному представлению. Также необходимо выполнить репликацию базовой таблицы.  
  
    -   **indexed view logbased manualfilter** — журнальная статья индексированного представления с горизонтальной фильтрацией, где хранимая процедура создается вручную и определяется пользователем в параметре `@filter`. Дополнительные сведения см. в разделе [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **indexed view logbased manualfilter** — журнальная статья индексированного представления с фильтрацией, где представление, определяющее вертикальную фильтрацию, создается и определяется пользователем вручную и указывается в параметре `@sync_object`. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **indexed view logbased manualboth** — журнальная статья индексированного представления с вертикальной и горизонтальной фильтрацией, где хранимая процедура для горизонтальной фильтрации и представление для вертикальной фильтрации создаются и определяются пользователем, а затем указываются в параметрах `@filter` и `@sync_object`. Дополнительные сведения см. в разделах [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) и [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Выполните процедуру **sp_articlefilter** для статей **logbased manualboth** и [logbased manualfilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) , чтобы создать хранимую процедуру фильтрации для статьи с горизонтальной фильтрацией. Дополнительные сведения см. в разделе [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Выполните процедуру **sp_articleview**для статей **logbased manualboth**, **logbased manualview** и [logbased manualfilter](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) , чтобы создать представление, определяющее статью с вертикальной фильтрацией. Дополнительные сведения см. в статье [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-stored-procedure-stored-procedure-execution-or-user-defined-function-article-in-a-transactional-or-snapshot-publication"></a>Публикация статьи хранимой процедуры, выполнение хранимой процедуры или определяемой пользователем функции в публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)на издателе в базе данных публикации. Чтобы определить тип статьи, укажите одно из следующих значений параметра `@type`:  
  
    -   **proc schema only** — статья со схемой, соответствующая хранимой процедуре.  
  
    -   **proc exec** — производит репликацию выполнения хранимой процедуры на всех подписчиках статьи. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **serializable proc exec** — производит репликацию выполнения хранимой процедуры только в том случае, если она выполняется в контексте сериализуемой транзакции. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **func schema only** — статья со схемой, соответствующая определяемой пользователем функции.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
### <a name="to-publish-a-table-or-view-article-in-a-merge-publication"></a>Публикация статьи таблицы или представления в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра `@type`:  
  
    -   **table** — статья таблицы.  
  
    -   **indexed view schema only** — статья со схемой, соответствующая индексированному представлению.  
  
    -   **view schema only** — статья со схемой, соответствующая представлению.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
### <a name="to-publish-a-stored-procedure-or-user-defined-function-article-in-a-merge-publication"></a>Публикация статьи хранимой процедуры или определяемой пользователем функции в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Чтобы определить тип статьи, укажите одно из следующих значений параметра `@type`:  
  
    -   **func schema only** — статья со схемой, соответствующая определяемой пользователем функции.  
  
    -   **proc schema only** — статья со схемой, соответствующая хранимой процедуре.  
  
     Таким образом определяется новая статья для публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
## <a name="see-also"></a>См. также:  
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
