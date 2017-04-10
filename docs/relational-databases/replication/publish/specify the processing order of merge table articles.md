---
title: "установить порядок обработки статей таблиц слияния (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
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
  - "статьи [репликация SQL Server], порядок обработки"
  - "репликация слиянием [репликация SQL Server], порядок обработки статей"
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# установить порядок обработки статей таблиц слияния (программирование репликации на языке Transact-SQL)
  Репликация слиянием позволяет указать порядок, в котором статьи обрабатываются агентом слияния во время процесса синхронизации. Можно с помощью хранимых процедур репликации программно назначить порядок каждой статье при ее создании. Статьи обрабатываются по номерам, от меньших к большим. Если значения двух статей совпадают, то эти статьи обрабатываются одновременно. Дополнительные сведения см. в разделе [Укажите обработки заказа из слияния статьи](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
### Указание порядка обработки для новой статьи публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите целое значение, представляющее порядок обработки статей для **@processing_order**. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  При создании упорядоченных статей необходимо оставлять промежутки между значениями порядковых номеров статей. Это облегчит задание новых значений в будущем. Например, если имеется три статьи, для которых необходимо указать фиксированный порядок обработки, значение **@processing_order** 10, 20 и 30, а не 1, 2 и 3 соответственно.  
  
### Изменение порядка обработки статьи публикации слиянием  
  
1.  Чтобы определить порядок обработки статей, выполните [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) и обратите внимание на значение **processing_order** в результирующем наборе.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение **processing_order** для **@property** и целочисленное значение, представляющее порядок обработки **@value**.  
  
## См. также:  
 [Указание порядка обработки статей публикации слиянием](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  