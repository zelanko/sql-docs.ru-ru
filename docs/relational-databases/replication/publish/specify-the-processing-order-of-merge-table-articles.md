---
title: Определение порядка обработки для статей таблиц слияния | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1bec5a8d14adf65bbf8df5d149e79b5299327c0c
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37348816"
---
# <a name="specify-the-processing-order-of-merge-table-articles"></a>Определение порядка обработки статей таблиц слияния
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликация слиянием позволяет указать порядок, в котором статьи обрабатываются агентом слияния во время процесса синхронизации. Можно с помощью хранимых процедур репликации программно назначить порядок каждой статье при ее создании. Статьи обрабатываются по номерам, от меньших к большим. Если значения двух статей совпадают, то эти статьи обрабатываются одновременно. Дополнительные сведения см. в статье [Определение порядка обработки для статей публикации слиянием](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>Указание порядка обработки для новой статьи публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите целое значение, представляющее порядок обработки статьи, в параметре **@processing_order**. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  При создании упорядоченных статей необходимо оставлять промежутки между значениями порядковых номеров статей. Это облегчит задание новых значений в будущем. Например, если существуют три статьи, для которых нужно указать фиксированный порядок обработки, укажите в параметре **@processing_order** значения 10, 20 и 30, а не 1, 2 и 3 соответственно.  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>Изменение порядка обработки статьи публикации слиянием  
  
1.  Чтобы определить порядок обработки статьи, выполните процедуру [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) и проверьте значение **processing_order** в результирующем наборе.  
  
2.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение из свойства **processing_order** в параметре **@property** и целое значение, представляющее порядок обработки, в параметре **@value**.  
  
## <a name="see-also"></a>См. также:  
 [Определение порядка обработки для статей публикации слиянием](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  
