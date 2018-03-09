---
title: "sp_certify_removable (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs:
- TSQL
helpviewer_keywords:
- sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4ca484db8104c1c1e817d08be0cf2a72ada76822
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spcertifyremovable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет, правильно ли настроена база данных для установочного или съемного носителя, и сообщает обо всех проблемах пользователю.  
  
> **ВАЖНО!** [! ВКЛЮЧИТЬ[ssNoteDepFutureAvoid](../../t-sql/statements/create-database-sql-server-transact-sql.md) вместо него.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@dbname=**] **'***dbname***'**  
 Указывает проверяемую базу данных. *DBName* — **sysname**.  
  
 [  **@autofix=**] **«auto»**  
 Делает системного администратора владельцем базы данных и всех ее объектов, а также удаляет все разрешения, не соответствующие разрешениям по умолчанию, и всех пользователей базы данных, созданных пользователями. *Auto* — **nvarchar(4)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Если база данных настроена правильно, **sp_certify_removable** выполняет следующее:  
  
-   Переводит базу данных в режим «вне сети», чтобы позволить копировать файлы.  
  
-   Обновляет статистику по всем таблицам и сообщает обо всех проблемах, связанных с владельцами и пользователями.  
  
-   Помечает файловые группы данных как «только для чтения», чтобы эти файлы можно было скопировать на носители, предназначенные только для чтения.  
  
 Владельцем базы данных и всех объектов базы данных должен быть системный администратор. Системный администратор — это пользователь, существующий на всех серверах, работающих под управлением [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и может быть должно существовать, если в базе данных распространения и установки.  
  
 При запуске **sp_certify_removable** без **автоматически** , она возвращает информацию о любом из следующих условий:  
  
-   Системный администратор не является владельцем базы данных.  
  
-   Существует хотя бы один пользователь, созданный пользователем.  
  
-   Системный администратор не является владельцем всех объектов базы данных.  
  
-   Были предоставлены разрешения, не соответствующие разрешениям по умолчанию.  
  
 Эти состояния можно исправить следующими способами:  
  
-   Используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства и процедуры, а затем выполните **sp_certify_removable** еще раз.  
  
-   Просто выполните **sp_certify_removable** с **автоматически** значение.  
  
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
 [sp_create_removable &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
