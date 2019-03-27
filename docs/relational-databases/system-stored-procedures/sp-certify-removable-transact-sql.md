---
title: sp_certify_removable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs:
- TSQL
helpviewer_keywords:
- sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 97964286b3281eee4e5b6850065c85034628bfdc
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493260"
---
# <a name="spcertifyremovable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет, правильно ли настроена база данных для установочного или съемного носителя, и сообщает обо всех проблемах пользователю.  
  
> **ВАЖНО!** [! ВКЛЮЧИТЬ[ssNoteDepFutureAvoid](../../t-sql/statements/create-database-sql-server-transact-sql.md) вместо этого.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'` Указывает проверяемую базу данных. *DBName* — **sysname**.  
  
`[ @autofix = ] 'auto'` Делает системного администратора владельцем базы данных и все объекты базы данных и удаляет все созданные пользователем базы данных пользователей и разрешений не по умолчанию. *Автоматическое* — **nvarchar(4)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если база данных настроена правильно, **sp_certify_removable** выполняет следующее:  
  
-   Переводит базу данных в режим «вне сети», чтобы позволить копировать файлы.  
  
-   Обновляет статистику по всем таблицам и сообщает обо всех проблемах, связанных с владельцами и пользователями.  
  
-   Помечает файловые группы данных как «только для чтения», чтобы эти файлы можно было скопировать на носители, предназначенные только для чтения.  
  
 Владельцем базы данных и всех объектов базы данных должен быть системный администратор. Системный администратор — это пользователь, существующая на всех серверах, работающих под управлением [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и должен существовать в базе данных распространения и установки.  
  
 При запуске **sp_certify_removable** без **автоматически** , она возвращает сведения о любом из следующих условий:  
  
-   Системный администратор не является владельцем базы данных.  
  
-   Существует хотя бы один пользователь, созданный пользователем.  
  
-   Системный администратор не является владельцем всех объектов базы данных.  
  
-   Были предоставлены разрешения, не соответствующие разрешениям по умолчанию.  
  
 Эти состояния можно исправить следующими способами:  
  
-   Используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства и процедуры, а затем выполните **sp_certify_removable** еще раз.  
  
-   Просто запустите **sp_certify_removable** с **автоматически** значение.  
  
 Обратите внимание, что эта хранимая процедура проверяет только пользователей и разрешения пользователей. К базе данных можно добавить группы и предоставить им разрешения. Дополнительные сведения см. в статье [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Выполнение разрешения ограничены членами **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 Следующий пример подтверждает, что база данных `inventory` готова к удалению.  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>См. также  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
