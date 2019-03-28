---
title: Хранимая процедура sp_dropmergealternatepublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergealternatepublisher
- sp_dropmergealternatepublisher_TSQL
helpviewer_keywords:
- sp_dropmergealternatepublisher
ms.assetid: a7dee4e2-2a60-41da-9d1d-6f991d7e2c5e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 368f16597a8060b5c1b9f2eb7fca5759bf8226b3
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532456"
---
# <a name="spdropmergealternatepublisher-transact-sql"></a>Хранимая процедура sp_dropmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет альтернативный издатель из публикации слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergealaternatepublisher [ @publisher = ] 'publisher'    , [ @publisher_db = ] 'publisher_db'    , [ @publication = ] 'publication'    , [ @alternate_publisher = ] 'alternate_publisher'    , [ @alternate_publisher_db = ] 'alternate_publisher_db'    , [ @alternate_publication = ] 'alternate_publication'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — Имя текущего издателя. *издатель*— **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя текущей базы данных публикации. *publisher_db*— **sysname**, не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'` — Имя текущей публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @alternate_publisher = ] 'alternate_publisher'` — Имя альтернативного издателя, которая будет удалена как альтернативного участника синхронизации. *alternate_publisher*— **sysname**, не имеет значения по умолчанию.  
  
`[ @alternate_publisher_db = ] 'alternate_publisher_db'` — Имя базы данных публикации, которая будет удалена как базы данных публикации альтернативного партнера. *alternate_publisher_db*— **sysname**, не имеет значения по умолчанию.  
  
`[ @alternate_publication = ] 'alternate_publication'` — Имя публикации, которая будет удалена как публикация альтернативного участника синхронизации. *alternate_publication*— **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **Хранимая процедура sp_dropmergealternatepublisher** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropmergelternatepublisher**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergealternatepublisher-transact-sql.md)  
  
  
