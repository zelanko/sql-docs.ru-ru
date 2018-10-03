---
title: Указание порядка обработки статей таблиц слияния (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c017a7e5dbc2d2eec535765c8889c68a16aad25b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146384"
---
# <a name="specify-the-processing-order-of-merge-table-articles-replication-transact-sql-programming"></a>установить порядок обработки статей таблиц слияния (программирование репликации на языке Transact-SQL)
  Репликация слиянием позволяет указать порядок, в котором статьи обрабатываются агентом слияния во время процесса синхронизации. Можно с помощью хранимых процедур репликации программно назначить порядок каждой статье при ее создании. Статьи обрабатываются по номерам, от меньших к большим. Если значения двух статей совпадают, то эти статьи обрабатываются одновременно. Дополнительные сведения см. в статье [Определение порядка обработки для статей публикации слиянием](../merge/specify-the-processing-order-of-merge-articles.md).  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>Указание порядка обработки для новой статьи публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите целое значение, представляющее порядок обработки статьи, в параметре **@processing_order**. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
    > [!NOTE]  
    >  При создании упорядоченных статей необходимо оставлять промежутки между значениями порядковых номеров статей. Это облегчит задание новых значений в будущем. Например, если существуют три статьи, для которых нужно указать фиксированный порядок обработки, укажите в параметре **@processing_order** значения 10, 20 и 30, а не 1, 2 и 3 соответственно.  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>Изменение порядка обработки статьи публикации слиянием  
  
1.  Чтобы определить порядок обработки статьи, выполните процедуру [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) и проверьте значение **processing_order** в результирующем наборе.  
  
2.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Укажите значение из свойства **processing_order** в параметре **@property** и целое значение, представляющее порядок обработки, в параметре **@value**.  
  
## <a name="see-also"></a>См. также  
 [Определение порядка обработки для статей публикации слиянием](../merge/specify-the-processing-order-of-merge-articles.md)  
  
  
