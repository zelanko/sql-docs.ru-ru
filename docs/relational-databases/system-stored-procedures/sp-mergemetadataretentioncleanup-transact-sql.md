---
description: sp_mergemetadataretentioncleanup (Transact-SQL)
title: sp_mergemetadataretentioncleanup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6f18a4f9357e3af6d9b120195dd13e187de95fd3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535137"
---
# <a name="sp_mergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Выполняет ручную очистку метаданных в системных таблицах [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)и [MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md) . Эта хранимая процедура выполняется на каждом издателе и подписчике в топологии.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @num_genhistory_rows = ] num_genhistory_rows OUTPUT` Возвращает число очищенных строк из таблицы [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md) . *num_genhistory_rows* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @num_contents_rows = ] num_contents_rows OUTPUT` Возвращает число очищенных строк из таблицы [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) . *num_contents_rows* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @num_tombstone_rows = ] num_tombstone_rows OUTPUT` Возвращает число очищенных строк из таблицы [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) . *num_tombstone_rows* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @aggressive_cleanup_only = ] aggressive_cleanup_only` Только для внутреннего использования.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
  
> [!IMPORTANT]  
>  Если в базе данных имеется несколько публикаций, а в любой из этих публикаций используется бесконечный срок хранения публикации, то выполнение **sp_mergemetadataretentioncleanup** не очищает метаданные отслеживания изменений репликации слиянием для базы данных. По этой причине, при использовании неограниченного срока хранения публикации необходимо помнить об осторожности. Чтобы определить, имеет ли публикация бесконечный срок хранения, выполните [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) на издателе и обратите внимание на все публикации в результирующем наборе со значением **0** для параметра **retention**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли базы данных **db_owner** или пользователи из списка доступа к публикации для опубликованной базы данных могут выполнять **sp_mergemetadataretentioncleanup**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
