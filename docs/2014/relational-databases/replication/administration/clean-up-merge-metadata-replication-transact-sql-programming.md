---
title: Очистка метаданных слияния (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 384b5cc158600848dbca6528a4c8c39250a23908
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62629174"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>очистить метаданные слияния (программирование репликации на языке Transact-SQL)
  Агент слияния периодически чистит метаданные репликации слиянием в зависимости от заданного срока хранения публикации. Это происходит на издателе и подписчике в системных таблицах [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)и [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) . Данные в этих таблицах могут чиститься и программным путем с помощью хранимых процедур репликации.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Очистка метаданных слияния вручную  
  
1.  В базе данных публикации на издателе выполните хранимую процедуру [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).  
  
2.  Используемых Обратите внимание на количество строк, удаленных на шаге 1 из системных таблиц [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)и [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) , возвращаемых соответственно в **@num_genhistory_rows**выходных **@num_contents_rows**параметрах **@num_tombstone_rows** , и.  
  
3.  Повторите шаги 1 и 2 на подписчике для очистки метаданных в базе данных подписки.  
  
## <a name="see-also"></a>См. также:  
 [Окончание срока действия и отключение подписки](../subscription-expiration-and-deactivation.md)  
  
  
