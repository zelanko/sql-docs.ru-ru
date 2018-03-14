---
title: "Определение порядка обработки для статей таблиц слияния | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1be2a5e6ecb84d1225d3101364ec881f74cb78bd
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="specify-the-processing-order-of-merge-table-articles"></a>Определение порядка обработки статей таблиц слияния
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликация слиянием позволяет указать порядок, в котором статьи обрабатываются агентом слияния во время процесса синхронизации. Можно с помощью хранимых процедур репликации программно назначить порядок каждой статье при ее создании. Статьи обрабатываются по номерам, от меньших к большим. Если значения двух статей совпадают, то эти статьи обрабатываются одновременно. Дополнительные сведения см. в статье [Определение порядка обработки для статей публикации слиянием](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>Указание порядка обработки для новой статьи публикации слиянием  
  
1.  В издателе в базе данных публикации выполните процедуру [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите целое значение, представляющее порядок обработки статьи, в параметре **@processing_order**. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  При создании упорядоченных статей необходимо оставлять промежутки между значениями порядковых номеров статей. Это облегчит задание новых значений в будущем. Например, если существуют три статьи, для которых нужно указать фиксированный порядок обработки, укажите в параметре **@processing_order** значения 10, 20 и 30, а не 1, 2 и 3 соответственно.  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>Изменение порядка обработки статьи публикации слиянием  
  
1.  Чтобы определить порядок обработки статьи, выполните процедуру [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) и проверьте значение **processing_order** в результирующем наборе.  
  
2.  В издателе в базе данных публикации выполните процедуру [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение из свойства **processing_order** в параметре **@property** и целое значение, представляющее порядок обработки, в параметре **@value**.  
  
## <a name="see-also"></a>См. также:  
 [Определение порядка обработки для статей публикации слиянием](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  
