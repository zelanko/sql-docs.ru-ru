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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 64621f1d675fc7cd4e64b690b1e440a1dbad2d1c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826691"
---
# <a name="sp_certify_removable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет, правильно ли настроена база данных для установочного или съемного носителя, и сообщает обо всех проблемах пользователю.  
  
> **ВАЖНО!** [! Включите вместо него[сснотедепфутуреавоид](../../t-sql/statements/create-database-sql-server-transact-sql.md) .  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'`Указывает проверяемую базу данных. Аргумент *dbname* имеет тип **sysname**.  
  
`[ @autofix = ] 'auto'`Предоставляет системному администратору право владения базой данных и всеми объектами базы данных, а также удаляет всех пользователей базы данных, созданных пользователем, и нестандартных разрешений. *Auto* имеет тип **nvarchar (4)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если база данных настроена правильно, **sp_certify_removable** выполняет следующие действия:  
  
-   Переводит базу данных в режим «вне сети», чтобы позволить копировать файлы.  
  
-   Обновляет статистику по всем таблицам и сообщает обо всех проблемах, связанных с владельцами и пользователями.  
  
-   Помечает файловые группы данных как «только для чтения», чтобы эти файлы можно было скопировать на носители, предназначенные только для чтения.  
  
 Владельцем базы данных и всех объектов базы данных должен быть системный администратор. Системный администратор является известным пользователем, который существует на всех выполняющихся серверах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и может ожидать существования при последующей распределении и установке базы данных.  
  
 Если вы запускаете **sp_certify_removable** без **автоматического** значения, он возвращает сведения о любом из следующих условий:  
  
-   Системный администратор не является владельцем базы данных.  
  
-   Существует хотя бы один пользователь, созданный пользователем.  
  
-   Системный администратор не является владельцем всех объектов базы данных.  
  
-   Были предоставлены разрешения, не соответствующие разрешениям по умолчанию.  
  
 Эти состояния можно исправить следующими способами:  
  
-   Используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства и процедуры, а затем снова запустите **sp_certify_removable** .  
  
-   Просто запустите **sp_certify_removable** с параметром **Auto** .  
  
 Обратите внимание, что эта хранимая процедура проверяет только пользователей и разрешения пользователей. К базе данных можно добавить группы и предоставить им разрешения. Дополнительные сведения см. в разделе [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение ограничены членами предопределенной роли сервера **sysadmin** .  
  
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
  
  
