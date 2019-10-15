---
title: sp_grantdbaccess (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grantdbaccess
- sp_grantdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantdbaccess
ms.assetid: 3eb09513-03f1-42f8-9917-3a1f3a579bec
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 3b88badb8b1852617d9edd8acd31f2c19258cca7
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304863"
---
# <a name="sp_grantdbaccess-transact-sql"></a>sp_grantdbaccess (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет нового пользователя в текущую базу данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] используйте вместо этого [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_grantdbaccess [ @loginame = ] 'login'  
    [ , [ @name_in_db = ] 'name_in_db' [ OUTPUT ] ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login_ '` — имя группы Windows, имя входа Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа для сопоставления с новым пользователем базы данных. Имена групп Windows и имен входа Windows должны быть дополнены именем домена Windows в формате *домен*\\*Login*; Например, **LONDON\Joeb**. Указанное имя входа не может быть уже сопоставлено с пользователем в базе данных. *имя входа* имеет тип **sysname**и не имеет значения по умолчанию.  
  
``[ @name_in_db = ] 'name_in_db' [ OUTPUT]`` — это имя нового пользователя базы данных. *name_in_db* — это выходная переменная с типом данных **sysname**и ЗНАЧЕНИЕМ по умолчанию NULL. Если значение не указано, используется *имя входа* . Если параметр указан как ВЫХОДная переменная со значением NULL, для параметра **\@name_in_db** задано значение *Login*. *name_in_db* уже не должен существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_grantdbaccess** вызывает CREATE USER, который поддерживает дополнительные параметры. Дополнительные сведения о создании пользователей базы данных см. в разделе [Create &#40;user&#41;Transact-SQL](../../t-sql/statements/create-user-transact-sql.md). Чтобы удалить пользователя базы данных из базы данных, используйте [инструкцию DROP USER](../../t-sql/statements/drop-user-transact-sql.md).  
  
 **sp_grantdbaccess** нельзя выполнить в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_accessadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере `CREATE USER` используется для добавления пользователя базы данных для имени входа Windows `Edmonds\LolanSo` в текущую базу данных. Новому пользователю присваивается имя `Lolan`. Этот метод является предпочтительным при создании пользователя базы данных.  
  
```sql
CREATE USER Lolan FOR LOGIN [Edmonds\LolanSo];  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [DROP USER (Transact-SQL)](../../t-sql/statements/drop-user-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
