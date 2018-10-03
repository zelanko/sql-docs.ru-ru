---
title: sp_restoremergeidentityrange (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c5e07b7dde01cc8e8a0c1289a25c8fd3de83aae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792132"
---
# <a name="sprestoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура используется для обновления присвоения диапазона идентификаторов. Она обеспечивает автоматическое и корректное управление диапазонами идентификаторов после восстановления издателя из резервной копии. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication** =] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию **все**. Если он указан, восстанавливаются диапазоны идентификаторов только для соответствующей публикации.  
  
 [ **@article** =] **"***статье***"**  
 Имя статьи. *статья* — **sysname**, со значением по умолчанию **все**. Если он указан, восстанавливаются диапазоны идентификаторов только для соответствующей статьи.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_restoremergeidentityrange** используется с репликацией слиянием.  
  
 **sp_restoremergeidentityrange** возвращает о выделении диапазонов идентификаторов максимальное из распространителя и обновляет значения в **max_used** столбец [MSmerge_identity_range_allocations &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) для статей, которые используют автоматическое управление диапазонами идентификаторов.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_restoremergeidentityrange**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
