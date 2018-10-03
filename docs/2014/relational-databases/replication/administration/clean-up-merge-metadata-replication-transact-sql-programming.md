---
title: Очистка метаданных слияния (программирование репликации на языке Transact-SQL) | Документация Майкрософт
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
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b559c7ea2f1cd882a9a737935416dbd5e1869187
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179484"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>очистить метаданные слияния (программирование репликации на языке Transact-SQL)
  Агент слияния периодически чистит метаданные репликации слиянием в зависимости от заданного срока хранения публикации. Это происходит на издателе и подписчике в системных таблицах [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)и [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) . Данные в этих таблицах могут чиститься и программным путем с помощью хранимых процедур репликации.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Очистка метаданных слияния вручную  
  
1.  В базе данных публикации на издателе выполните хранимую процедуру [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).  
  
2.  Обратите внимание на то, что количество строк , удаляемых в шаге 1 из системных таблиц [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)и [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) , выводится, соответственно, в выходных параметрах **@num_genhistory_rows**, **@num_contents_rows**и **@num_tombstone_rows** (необязательно).  
  
3.  Повторите шаги 1 и 2 на подписчике для очистки метаданных в базе данных подписки.  
  
## <a name="see-also"></a>См. также  
 [Окончание срока действия и отключение подписки](../subscription-expiration-and-deactivation.md)  
  
  
