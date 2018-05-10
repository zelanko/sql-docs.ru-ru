---
title: ALTER USER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_USER_TSQL
- ALTER USER
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database users
- ALTER USER statement
- renaming databases
- schemas [SQL Server], default
- database user names [SQL Server]
- names [SQL Server], database users
- default schemas
- modifying default schemas
ms.assetid: 344fc6ce-a008-47c8-a02e-47fae66cc590
caps.latest.revision: 75
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: aafcc77a26dcd75c5581f36acc8e37cd852684a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="alter-user-transact-sql"></a>ALTER USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Переименовывает пользователя базы данных или изменяет его схему, используемую по умолчанию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
[;]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = { schemaName | NULL }  
    | LOGIN = loginName  
    | PASSWORD = 'password' [ OLD_PASSWORD = 'oldpassword' ]  
    | DEFAULT_LANGUAGE = { NONE | <lcid> | <language name> | <language alias> }  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = schemaName  
    | LOGIN = loginName  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]   
[;]  
  
-- Azure SQL Database Update Syntax  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
[;]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = { schemaName | NULL }  
    | LOGIN = loginName  
    | PASSWORD = 'password' [ OLD_PASSWORD = 'oldpassword' ]  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]   
  
-- SQL Database syntax when connected to a federation member  
ALTER USER userName  
     WITH <set_item> [ ,… n ]   
[;]  
  
<set_item> ::=   
     NAME = newUserName  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
     NAME =newUserName   
     | LOGIN =loginName  
     | DEFAULT_SCHEMA = schema_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *userName*  
 Указывает имя, по которому пользователь идентифицируется в этой базе данных.  
  
 LOGIN **=***loginName*  
 Сопоставляет пользователя с другим именем входа, заменив идентификатор безопасности пользователя для соответствия идентификатору безопасности имени входа.  
  
 Если инструкция ALTER USER — единственная в пакете SQL, то база данных SQL Windows Azure поддерживает предложение WITH LOGIN. Если инструкция ALTER USER не единственная в пакете SQL или выполняется в динамическом коде SQL, предложение WITH LOGIN не поддерживается.  
  
 NAME **=***newUserName*  
 Задает новое имя для этого пользователя. Аргумент *newUserName* еще не должен существовать в текущей базе данных.  
  
 DEFAULT_SCHEMA **=** { *schemaName* | NULL }  
 Задает первую схему для поиска сервером, когда он разрешает имена объектов для этого пользователя. При установке схемы по умолчанию в значение NULL схема по умолчанию удаляется из группы Windows.   Параметр NULL нельзя использовать с пользователем Windows.  
  
 PASSWORD **=** '*password*'  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Указывает пароль для пользователя, которого необходимо изменить. В паролях учитывается регистр символов.  
  
> [!NOTE]  
>  Данный параметр доступен только для содержащихся пользователей. Дополнительные сведения см. в разделах [Автономные базы данных](../../relational-databases/databases/contained-databases.md) и [sp_migrate_user_to_contained (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md).  
  
 OLD_PASSWORD **=***'oldpassword'*  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Текущий пароль пользователя, который будет заменен на "*password*". В паролях учитывается регистр символов. Параметр *OLD_PASSWORD* является обязательным для изменения пароля. Изменить пароль без этого параметра можно только при наличии разрешения **ALTER ANY USER**. Необходимость указать *OLD_PASSWORD* не позволит пользователям с разрешением **IMPERSONATION** изменить пароль.  
  
> [!NOTE]  
>  Данный параметр доступен только для содержащихся пользователей.  
  
 DEFAULT_LANGUAGE **=***{ NONE | \<lcid> | \<language name> | \<language alias> }*  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает язык по умолчанию, присвоенный пользователю. Если этот параметр установлен в значение NONE, то в качестве языка по умолчанию выбирается текущий язык по умолчанию для базы данных. При последующей смене языка по умолчанию для базы данных язык по умолчанию для пользователя не меняется. Аргумент *DEFAULT_LANGUAGE* может быть идентификатором локали (lcid), названием языка или псевдонимом языка.  
  
> [!NOTE]  
>  Этот параметр можно задать только в автономной базе данных и только для содержащихся пользователей.  
  
 ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | **OFF** ] ]  
 **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Отключает проверки шифрованных метаданных на сервере в операциях массового копирования. Это позволяет пользователю массово копировать зашифрованные данные между таблицами или базами данных без расшифровки данных. Значение по умолчанию — OFF.  
  
> [!WARNING]  
>  Неправильное использование этого параметра может привести к повреждению данных. Дополнительные сведения см. в разделе [Перенос конфиденциальных данных с помощью функции Always Encrypted](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).  
  
## <a name="remarks"></a>Примечания  
 Схемой по умолчанию будет первая схема, которую найдет сервер, после того как получит имена объектов для данного пользователя базы данных. Если не указано иное, схемой по умолчанию будет владелец объектов, создаваемых этим пользователем базы данных.  
  
 Если пользователь имеет схему по умолчанию, будет использоваться эта схема. Если у пользователя нет схемы по умолчанию, но он является членом группы, которая имеет схему по умолчанию, используется схема по умолчанию группы. Если пользователь не имеет схемы по умолчанию и является членом нескольких групп, схемой по умолчанию для этого пользователя будет схема по умолчанию группы Windows с минимальным значением principal_id и явно заданной схемой по умолчанию. Если для пользователя нельзя определить схему по умолчанию, будет использоваться схема **dbo**.  
  
 В качестве значения DEFAULT_SCHEMA можно задать схему, которая в настоящий момент не существует в базе данных. Поэтому значение DEFAULT_SCHEMA можно определить для пользователя еще до создания схемы.  
  
 Значение DEFAULT_SCHEMA не может быть указано для пользователя, сопоставленного с сертификатом или асимметричным ключом.  
  
> [!IMPORTANT]  
>  Значение параметра DEFAULT_SCHEMA не учитывается, если пользователь является членом предопределенной роли сервера **sysadmin**. Для всех членов роли сервера **sysadmin** по умолчанию установлена схема `dbo`.  
  
 Имя пользователя, сопоставленное с именем входа или группой Windows, можно изменить только в том случае, если значение идентификатора безопасности имени нового пользователя совпадает с уже записанным в базе данных. Такая проверка предотвращает имитацию подключения к базе данных с помощью имен входа Windows.  
  
 Предложение WITH LOGIN позволяет сопоставить пользователя с другим именем входа. Пользователи, не имеющие имени входа, а также пользователи, сопоставленные с сертификатом или с асимметричным ключом, не могут быть повторно сопоставлены с помощью этого предложения. Возможно повторное сопоставление только пользователей (или групп) SQL и Windows. Предложение WITH LOGIN не может быть использовано для изменения типа пользователя, например для перехода от учетной записи Windows на имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Имя пользователя будет автоматически изменено на имя входа, если удовлетворяются следующие условия.  
  
-   Пользователь является пользователем Windows.  
  
-   Имя является именем Windows (содержит обратную косую черту).  
  
-   Новое имя не было указано.  
  
-   Текущее имя отличается от имени входа.  
  
 В противном случае пользователь не будет переименован, если только вызывающий не вызовет дополнительно предложение NAME.  
  
Имя пользователя, сопоставленное с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сертификатом или асимметричным ключом, не может содержать обратную косую черту (\\).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="security"></a>Безопасность  
  
> [!NOTE]  
>  Пользователь с разрешением **ALTER ANY USER** может изменить схему по умолчанию для любого пользователя. Пользователь с измененной схемой может производить выборку данных неизвестным образом из неправильной таблицы или выполнять код из неправильной схемы.  
  
### <a name="permissions"></a>Разрешения  
 Чтобы изменить имя пользователя, необходимо разрешение **ALTER ANY USER** для базы данных.  
  
 Чтобы изменить целевое имя входа пользователя, необходимо разрешение **CONTROL** в базе данных.  
  
 Чтобы изменить имя пользователя с разрешением **CONTROL** в базе данных, требуется разрешение **CONTROL** в базе данных.  
  
 Чтобы изменить схему или язык по умолчанию, требуется разрешение **ALTER** на пользователя. Пользователь может изменить свою собственную схему или язык по умолчанию.  
  
## <a name="examples"></a>Примеры  

Все примеры выполняются в базе данных пользователя.  

### <a name="a-changing-the-name-of-a-database-user"></a>A. Изменение имени пользователя базы данных  
 В следующем примере показано изменение имени пользователя базы данных с `Mary5` на `Mary51`.  
  
```  
ALTER USER Mary5 WITH NAME = Mary51;  
GO  
```  
  
### <a name="b-changing-the-default-schema-of-a-user"></a>Б. Изменение схемы пользователя, используемой по умолчанию  
 В данном примере показано изменение схемы пользователя, используемой по умолчанию, с `Mary51` на `Purchasing`.  
  
```  
ALTER USER Mary51 WITH DEFAULT_SCHEMA = Purchasing;  
GO  
```  
  
### <a name="c-changing-several-options-at-once"></a>В. Изменение нескольких параметров одновременно  
 В следующем примере несколько параметров пользователя автономной базы данных изменяются одной инструкцией.  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
ALTER USER Philip   
WITH  NAME = Philipe   
    , DEFAULT_SCHEMA = Development   
    , PASSWORD = 'W1r77TT98%ab@#’ OLD_PASSWORD = 'New Devel0per'   
    , DEFAULT_LANGUAGE  = French ;  
GO  
```  
  
  
## <a name="see-also"></a>См. также  
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [DROP USER (Transact-SQL)](../../t-sql/statements/drop-user-transact-sql.md)   
 [Автономные базы данных](../../relational-databases/databases/contained-databases.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_migrate_user_to_contained (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md)  
  
  


