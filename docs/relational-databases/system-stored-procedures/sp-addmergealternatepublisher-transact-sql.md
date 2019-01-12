---
title: sp_addmergealternatepublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergealternatepublisher_TSQL
- sp_addmergealternatepublisher
helpviewer_keywords:
- sp_addmergealternatepublisher
ms.assetid: de46e0b1-d946-4021-bff6-2d8e3187656d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21d0ea34f3521333976ce00a3f5b823c3fcb816a
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129304"
---
# <a name="spaddmergealternatepublisher-transact-sql"></a>sp_addmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет подписчику возможность использовать альтернативного партнера синхронизации. В свойствах публикации должно быть указано, что подписчики могут синхронизироваться с другими издателями. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergealternatepublisher [ @publisher= ] 'publisher'  
          , [ @publisher_db= ] 'publisher_db'  
          , [ @publication= ] 'publication'  
          , [ @alternate_publisher= ] 'alternate_synchronization_partner'  
          , [ @alternate_publisher_db= ] 'alternate_publisher_db'  
          , [ @alternate_publication= ] 'alternate_synchronization_partner'  
     , [ @alternate_distributor= ] 'alternate_distributor'   
    [ , [ @friendly_name= ] 'friendly_name' ]   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"**_издателя_**"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=**] **"**_publisher_db_**"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication=**] **"**_публикации_**"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_publisher=**] **"**_alternate_synchronization_partner_**"**  
 Имя альтернативного издателя. *alternate_synchronization_partner* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_publisher_db=**] **"**_alternate_publisher_db_**"**  
 Имя базы данных публикации на сервере альтернативного издателя. *alternate_publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_publication=**] **"**_alternate_synchronization_partner_**"**  
 Имя базы данных публикации на сервере альтернативного участника синхронизации. *alternate_synchronization_partner* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_distributor=**] **"**_alternate_distributor_**"**  
 Имя распространителя для альтернативного участника синхронизации. *alternate_distributor* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@friendly_name=**] **"**_friendly_name_**"**  
 Отображаемое имя, по которому можно идентифицировать ассоциацию издателя, публикации и распространителя в качестве альтернативного участника синхронизации. *Аргумент* — **nvarchar(255)**, значение по умолчанию NULL.  
  
 [  **@reserved=**] **"**_зарезервированные_**"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergealternatepublisher** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergealternatepublisher**.  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_dropmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergealternatepublisher-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
