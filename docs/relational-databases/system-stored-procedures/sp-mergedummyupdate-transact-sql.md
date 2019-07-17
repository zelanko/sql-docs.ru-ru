---
title: sp_mergedummyupdate (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergedummyupdate_TSQL
- sp_mergedummyupdate
helpviewer_keywords:
- sp_mergedummyupdate
ms.assetid: b834f7f6-9588-4d59-a3e2-83d8e8e722e1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 209a41ff29f8063ec6c46fe1fb5e821be1419cd6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019978"
---
# <a name="spmergedummyupdate-transact-sql"></a>sp_mergedummyupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Производит фиктивное обновление данной строки, чтобы вновь переслать ее в ходе следующего объединения. Эта хранимая процедура может выполняться на издателе в базе данных публикации или на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_mergedummyupdate [ @source_object =] 'source_object', [ @rowguid =] 'rowguid'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @source_object = ] 'source_object'` — Имя исходного объекта. *source_object*— **nvarchar(386)** , не имеет значения по умолчанию.  
  
`[ @rowguid = ] 'rowguid'` — Это идентификатор строки. *ROWGUID* — **uniqueidentifier**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_mergedummyupdate** используется в репликации слиянием.  
  
 **sp_mergedummyupdate** полезно, если вы пишете собственный вариант, чтобы средство просмотра конфликтов репликации (Wzcnflct.exe).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_mergedummyupdate**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
