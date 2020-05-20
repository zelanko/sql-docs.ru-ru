---
title: sp_restoremergeidentityrange (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a41b725d46c96f1ab79444246ab538b0c3f539f0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82817005"
---
# <a name="sp_restoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура используется для обновления присвоения диапазона идентификаторов. Она обеспечивает автоматическое и корректное управление диапазонами идентификаторов после восстановления издателя из резервной копии. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение **ALL**по умолчанию. Если он указан, восстанавливаются диапазоны идентификаторов только для соответствующей публикации.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и значение по умолчанию **ALL**. Если он указан, восстанавливаются диапазоны идентификаторов только для соответствующей статьи.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_restoremergeidentityrange** используется с репликацией слиянием.  
  
 **sp_restoremergeidentityrange** получает максимальные сведения о выделении диапазона идентификаторов от распространителя и обновляет значения в столбце **max_used** в [MSmerge_identity_range_allocations &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) для статей, использующих автоматическое управление диапазонами идентификаторов.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_restoremergeidentityrange**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
