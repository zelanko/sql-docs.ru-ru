---
title: sp_mergemetadataretentioncleanup (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4ac0c7820ab4f336057a3d747409b0e1af09248d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32996091"
---
# <a name="spmergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выполняет ручную очистку метаданных в [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_ сопоставления](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), и [MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md) системных таблиц. Эта хранимая процедура выполняется на каждом издателе и подписчике в топологии.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@num_genhistory_rows=** ] *num_genhistory_rows* выходных данных  
 Возвращает число строк, очищенных от [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md) таблицы. *num_genhistory_rows* — **int**, значение по умолчанию **0**.  
  
 [  **@num_contents_rows=** ] *num_contents_rows* выходных данных  
 Возвращает число строк, очищенных от [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) таблицы. *num_contents_rows* — **int**, значение по умолчанию **0**.  
  
 [  **@num_tombstone_rows=** ] *num_tombstone_rows* выходных данных  
 Возвращает число строк, очищенных от [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) таблицы. *num_tombstone_rows* — **int**, значение по умолчанию **0**.  
  
 [  **@aggressive_cleanup_only=** ] *aggressive_cleanup_only*  
 Только для внутреннего применения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  Если имеется несколько публикаций в базе данных, а один из этих публикаций использует бесконечный срок хранения публикации, на котором запущен **sp_mergemetadataretentioncleanup** не очистки отслеживания изменений репликации слиянием метаданные для базы данных. По этой причине, при использовании неограниченного срока хранения публикации необходимо помнить об осторожности. Чтобы определить, имеет ли публикация неограниченный срок хранения, выполните [sp_helpmergepublication &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) на издателе и обратите внимание любых публикаций в результирующий набор со значением **0** для **хранения**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** фиксированной роли базы данных или пользователей в список доступа к публикации для опубликованной базы данных можно выполнить **sp_mergemetadataretentioncleanup**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
