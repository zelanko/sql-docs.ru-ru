---
title: sp_copysnapshot (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords:
- sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 429a0c439f5257989e6fb7e85d34a8ea576ad41a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526996"
---
# <a name="spcopysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Копирует папку моментальных снимков указанной публикации в папку, указанную в **@destination_folder**. Эта хранимая процедура выполняется на издателе в базе данных публикации. Данная хранимая процедура полезна для копирования моментального снимка на извлекаемые носители, такие как CD-ROM.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, должны быть скопированы, содержимое моментального снимка. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @destination_folder = ] 'destination_folder'` — Имя папки, в которой должны копироваться содержимое моментального снимка публикации. *destination_folder*is **nvarchar(255)**, with no default. *Папка_назначения* может быть альтернативное расположение, например, на другом сервере, на сетевом диске или на съемном носителе (например, компакт-диски или съемные диски).  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* имеет тип sysname и значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db* имеет тип sysname и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_copysnapshot** используется во всех типах репликации. Подписчики, использующие [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 и более ранних версий не могут использовать альтернативное расположение моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_copysnapshot**.  
  
## <a name="see-also"></a>См. также  
 [Альтернативные расположения папки моментальных снимков](../../relational-databases/replication/snapshot-options.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
