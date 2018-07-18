---
title: ALTER AUTHORIZATION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_AUTHORIZATION_TSQL
- ALTER AUTHORIZATION
dev_langs:
- TSQL
helpviewer_keywords:
- owners [SQL Server], transferring
- modifying entity ownership
- full-text search [SQL Server], permissions
- owners [SQL Server], entities
- ALTER AUTHORIZATION statement
- entity ownership [SQL Server]
- transferring ownership
- search property lists [SQL Server], permissions
- TAKE OWNERSHIP
ms.assetid: 8c805ae2-91ed-4133-96f6-9835c908f373
caps.latest.revision: 84
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1d1ff4bfeb848cf4f668d7e48a3cd3b574052ecc
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37786215"
---
# <a name="alter-authorization-transact-sql"></a>ALTER AUTHORIZATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет владельца защищаемой сущности.    
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Синтаксис    
    
```    
-- Syntax for SQL Server  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
        OBJECT | ASSEMBLY | ASYMMETRIC KEY | AVAILABILITY GROUP | CERTIFICATE     
      | CONTRACT | TYPE | DATABASE | ENDPOINT | FULLTEXT CATALOG     
      | FULLTEXT STOPLIST | MESSAGE TYPE | REMOTE SERVICE BINDING    
      | ROLE | ROUTE | SCHEMA | SEARCH PROPERTY LIST | SERVER ROLE     
      | SERVICE | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

```
-- Syntax for SQL Database  
  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
      OBJECT | ASSEMBLY | ASYMMETRIC KEY | CERTIFICATE     
    | TYPE | DATABASE | FULLTEXT CATALOG     
    | FULLTEXT STOPLIST     
    | ROLE | SCHEMA | SEARCH PROPERTY LIST     
    | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

    
```    
-- Syntax for Azure SQL Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
```    
-- Syntax for Parallel Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      DATABASE     
    | SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      database_name 
    | schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
## <a name="arguments"></a>Аргументы    
\<class_type> Защищаемый класс сущности, для которой изменяется владелец. По умолчанию это класс OBJECT.    
    
|||    
|-|-|    
|OBJECT|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], хранилище данных SQL Azure, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|ASSEMBLY|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ASYMMETRIC KEY|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|AVAILABILITY GROUP |**ПРИМЕНИМО К**: SQL Server 2012 до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|CERTIFICATE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|CONTRACT|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|DATABASE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION для баз данных](#AlterDB) ниже.|    
|ENDPOINT|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|FULLTEXT CATALOG|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|FULLTEXT STOPLIST|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|MESSAGE TYPE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|REMOTE SERVICE BINDING|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|ROLE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ROUTE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SCHEMA|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], хранилище данных SQL Azure, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|SEARCH PROPERTY LIST|**ПРИМЕНИМО К**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|SERVER ROLE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SERVICE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SYMMETRIC KEY|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|TYPE|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|XML SCHEMA COLLECTION|**ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
    
 *entity_name*    
 Имя сущности.    
    
 *principal_name* | SCHEMA OWNER    
 Имя субъекта безопасности, который будет являться собственником сущности.  Объекты базы данных должны принадлежать субъекту базы данных; пользователю базы данных или роли.  Объекты сервера (такие как базы данных) должны принадлежать субъекту сервера (имя для входа). Определите **SCHEMA OWNER** в качестве *principal_name*, чтобы показать, что объект должен принадлежать участнику, который владеет схемой объекта.    
    
## <a name="remarks"></a>Remarks    
 Инструкция ALTER AUTHORIZATION может использоваться для изменения владельца любой сущности, у которой он есть. Владение содержащимися в базе данных сущностями можно передать любому участнику уровня базы данных. Владение сущностями уровня сервера можно передать только участникам уровня сервера.    
    
> [!IMPORTANT]    
>  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], пользователь может владеть объектом (OBJECT) или типом (TYPE), содержащимся в схеме, которая принадлежит другому пользователю базы данных. Это поведение было изменено по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделах [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md) и [TYPEPROPERTY (Transact-SQL)](../../t-sql/functions/typeproperty-transact-sql.md).    
    
 Владение можно передавать для следующих, содержащихся в схемах сущностей типа «объект»: таблиц, представлений, функций, процедур, очередей и синонимов.    
    
 Нельзя передавать владение для следующих сущностей: связанных серверов, статистики, ограничений, правил, значений по умолчанию, триггеров, очередей компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], учетных данных, функций секционирования, схем секционирования, главных ключей баз данных, главного ключа службы, а также для уведомлений о событиях.    
    
 Нельзя передавать владение элементами следующих защищаемых классов: сервером, именем входа, пользователем, ролью приложения и столбцом.    
    
 Аргумент SCHEMA OWNER допустим только в случае передачи владения сущностью, содержащейся в схеме. Аргумент SCHEMA OWNER позволяет передать владение сущностью владельцу схемы, в которой она находится. В схемах содержатся только сущности классов OBJECT, TYPE или XML SCHEMA COLLECTION.    
    
 Если целевая сущность не представляет собой базу данных, а передаваемая сущность передается новому владельцу, все разрешения на целевую сущность удаляются.    
    
> [!CAUTION]    
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] поведение схем отличается от более ранних версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Код, предполагающий, что схемы эквивалентны пользователям базы данных, может возвращать неверные результаты. Старые представления каталогов, включая sysobjects, не должны использоваться в базах данных, где когда-либо выполнялась любая из следующих инструкций DDL: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. В базе данных, в которой когда-либо выполнялась любая из этих инструкций, необходимо использовать новые представления каталога. В новых представлениях каталогов учитывается разделение участников и схем, введенное в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения о представлениях каталогов см. в статье [Представления каталогов (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).    
    
 Имейте в виду следующее:    
    
> [!IMPORTANT]    
>  Единственный надежный способ найти владельца объекта — запросить представление каталога **sys.objects**. Единственный надежный способ найти владельца типа — использовать функцию TYPEPROPERTY.    
    
## <a name="special-cases-and-conditions"></a>Особые случаи и условия    
 В следующей таблице перечислены особые случаи, исключения и условия, касающиеся изменения авторизации.    
    
|Class|Условие|    
|-----------|---------------|    
|OBJECT|Нельзя изменить владельца триггеров, ограничений, правил, значений по умолчанию, статистик, системных объектов, очередей, индексированных представлений и таблиц с индексированными представлениями.|    
|SCHEMA|При передаче владения разрешения на содержащиеся в схеме объекты, у которых нет явных владельцев, удаляются. Нельзя изменить владельца схем sys, dbo и information_schema.|    
|TYPE|Нельзя изменить владельца сущности TYPE, принадлежащей схеме sys или information_schema.|    
|CONTRACT, MESSAGE TYPE или SERVICE|Нельзя изменить владельца системных сущностей.|    
|SYMMETRIC KEY|Нельзя изменить владельца глобальных временных ключей.|    
|CERTIFICATE или ASYMMETRIC KEY|Нельзя передавать владение данными сущностями роли или группе.|    
|ENDPOINT|Участник должен представлять собой имя входа в систему.|    
  
## <a name="AlterDB"></a> ALTER AUTHORIZATION для баз данных  
**ПРИМЕНИМО К**: [!INCLUDE[ssSQL15](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
### <a name="for-sql-server"></a>Для SQL Server:  
**Требования к новому владельцу:**   
Новый участник-владелец должен быть одним из следующих:  
-   имя входа для проверки подлинности SQL Server;  
-   имя входа для проверки подлинности Windows, представляющее пользователя Windows (а не группу);  
-   пользователь Windows, проходящий проверку подлинности с использованием имени входа для проверки подлинности Windows, представляющего группу Windows.  
  
**Требования к пользователю, выполняющему инструкцию ALTER AUTHORIZATION**  
Если вы не являетесь членом предопределенной роли сервера **sysadmin**, вам требуется как минимум разрешение TAKE OWNERSHIP для базы данных и разрешение IMPERSONATE для имени входа нового владельца.   

### <a name="for-azure-sql-database"></a>Для базы данных SQL Azure  
**Требования к новому владельцу:**   
Новый участник-владелец должен быть одним из следующих:  
-   имя входа для проверки подлинности SQL Server;  
-   федеративный пользователь (не группа) в Azure AD;  
-   управляемый пользователь (не группа) или приложение в Azure AD.    

> [!NOTE]  
> Если новый владелец является пользователем Azure Active Directory, он не может существовать как пользователь в базе данных, где новый владелец станет новым DBO. Такого пользователя Azure AD необходимо удалить из базы данных перед выполнением инструкции ALTER AUTHORIZATION, указав в качестве владельца базы данных нового пользователя. Дополнительные сведения о настройке пользователей Azure Active Directory с базой данных SQL см. в статье [Подключение к базе данных SQL или хранилищу данных SQL с использованием аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
**Требования к пользователю, выполняющему инструкцию ALTER AUTHORIZATION**  
Необходимо подключиться к целевой базе данных, чтобы изменить ее владельца.  

Изменить владельца базы данных могут следующие типы учетных записей. 
* Имя входа участника уровня службы. (Администратор SQL Azure, подготовленный при создании логического сервера.)  
* Администратор Active Directory для Azure SQL Server.   
* Текущий владелец базы данных.   
 
  
Следующая таблица содержит сводку требований.  
  
Исполнитель  |Назначение  |Результат    
---------|---------|---------  
Имя входа для проверки подлинности SQL Server     |Имя входа для проверки подлинности SQL Server         |Успешно  
Имя входа для проверки подлинности SQL Server     |Пользователь Azure AD         |Ошибка           
Пользователь Azure AD     |Имя входа для проверки подлинности SQL Server         |Успешно           
Пользователь Azure AD     |Пользователь Azure AD         |Успешно           
  
Чтобы проверить владельца базы данных Azure AD, выполните следующую команду Transact-SQL в базе данных пользователя (в этом примере `testdb`).  
    
```    
SELECT CAST(owner_sid as uniqueidentifier) AS Owner_SID   
FROM sys.databases   
WHERE name = 'testdb';  
```    
    
Выходными данными будет идентификатор (например, 6D8B81F6-7C79-444C-8858-4AF896C03C67), который соответствует ObjectID Azure AD, назначенному `richel@cqclinic.onmicrosoft.com`.  
Если владельцем базы данных SQL Server является пользователь имени входа, выполните следующую инструкцию в базе данных master для проверки владельца базы данных:  
    
```    
SELECT d.name, d.owner_sid, sl.name   
FROM sys.databases AS d  
JOIN sys.sql_logins AS sl  
ON d.owner_sid = sl.sid;  
    
```    
  
### <a name="best-practice"></a>Рекомендации  
  
Не используйте пользователей Azure AD в качестве отдельных владельцев базы данных — используйте группу Azure AD как член предопределенной роли базы данных **db_owner**. Далее приводятся действия по настройке имени входа в качестве владельца базы данных и назначению группы Azure Active Directory (`mydbogroup`) в качестве члена роли **db_owner**. 
1.  Войдите в SQL Server как администратор Azure AD и измените владельца базы данных на отключенное имя входа для проверки подлинности SQL Server. Например, в базе данных пользователя выполните следующую команду:  
  ```    
  ALTER AUTHORIZATION ON database::testdb TO DisabledLogin;  
  ```    
2.  Создайте группу Azure AD, которая должна быть владельцем базы данных, и добавьте ее в качестве пользователя в базу данных пользователя. Пример:  
  ```    
  CREATE USER [mydbogroup] FROM EXTERNAL PROVIDER;  
  ```    
3.  В базе данных добавьте пользователя, представляющего группу Azure AD, в предопределенную роль базы данных **db_owner**. Пример:  
  ```    
  ALTER ROLE db_owner ADD MEMBER mydbogroup;  
  ```    
  
Теперь члены `mydbogroup` могут централизованно управлять базой данных как члены роли **db_owner**.  
- Когда члены этой группы удаляются из группы Azure AD, они автоматически теряют разрешения dbo на эту базу данных.  
- Аналогичным образом новые члены, добавляемые в группу Azure AD `mydbogroup`, автоматически получают доступ dbo для этой базы данных.  
  
Чтобы проверить наличие действующего разрешения dbo у конкретного пользователя, пользователь должен выполнить следующую инструкцию:  
    
```    
SELECT IS_MEMBER ('db_owner');  
```    
  
Возвращаемое значение 1 указывает, что пользователь является членом роли.  
   
    
## <a name="permissions"></a>Разрешения    
 Требует разрешения TAKE OWNERSHIP для сущности. Если новый владелец не является пользователем, выполняющим данную инструкцию, также требуется одно из следующих условий: 1) разрешение IMPERSONATE для нового владельца, если это пользователь или имя входа; 2) если новый владелец представляет собой роль — членство в роли или разрешение ALTER для этой роли; 3) если новый владелец представляет собой роль приложения — разрешение ALTER для роли приложения.    
    
## <a name="examples"></a>Примеры    
    
### <a name="a-transfer-ownership-of-a-table"></a>A. Передача владения таблицей    
 В следующем примере владение таблицей `Sprockets` передается пользователю `MichikoOsada`. Эта таблица расположена в схеме `Parts`.    
    
```    
ALTER AUTHORIZATION ON OBJECT::Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 Запрос также может выглядеть следующим образом:    
    
```    
ALTER AUTHORIZATION ON Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 Если объекты схемы не включены в инструкцию, [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполнит поиск объекта в схеме пользователей по умолчанию. Пример:    
    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
```    
    
### <a name="b-transfer-ownership-of-a-view-to-the-schema-owner"></a>Б. Передача владения представлением владельцу схемы    
 В следующем примере передается владение представлением `ProductionView06` владельцу содержащей его схемы. Это представление расположено в схеме `Production`.    
    
```    
ALTER AUTHORIZATION ON OBJECT::Production.ProductionView06 TO SCHEMA OWNER;    
GO    
```    
    
### <a name="c-transfer-ownership-of-a-schema-to-a-user"></a>В. Передача владения схемой пользователю    
 В следующем примере владение схемой `SeattleProduction11` передается пользователю `SandraAlayo`.    
    
```    
ALTER AUTHORIZATION ON SCHEMA::SeattleProduction11 TO SandraAlayo;    
GO    
```    
    
### <a name="d-transfer-ownership-of-an-endpoint-to-a-sql-server-login"></a>Г. Передача владения конечной точкой имени входа в SQL Server    
 В следующем примере владение конечной точкой `CantabSalesServer1` передается `JaePak`. Так как конечная точка представляет собой защищаемую сущность уровня сервера, ее можно передать только участнику уровня сервера.    
    
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].    
    
```    
ALTER AUTHORIZATION ON ENDPOINT::CantabSalesServer1 TO JaePak;    
GO    
```    
    
### <a name="e-changing-the-owner-of-a-table"></a>Д. Изменение владельца таблицы    
 В каждом из следующих примеров показано изменение владельца таблицы `Sprockets` в базе данных `Parts` на пользователя базы данных `MichikoOsada`.    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON dbo.Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::dbo.Sprockets TO MichikoOsada;    
```    
    
### <a name="f-changing-the-owner-of-a-database"></a>Е. Изменение владельца базы данных    
 **ПРИМЕНИМО К**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].    
    
 В следующем примере показано, как изменить владельца базы данных `Parts` на имя входа `MichikoOsada`.    
    
```    
ALTER AUTHORIZATION ON DATABASE::Parts TO MichikoOsada;    
```    
  
### <a name="g-changing-the-owner-of-a-sql-database-to-an-azure-ad-user"></a>Ж. Изменение владельца базы данных SQL на пользователя Azure AD  
В следующем примере администратор Azure Active Directory для SQL Server в организации с Active Directory `cqclinic.onmicrosoft.com` может изменить текущую принадлежность базы данных `targetDB` и сделать пользователя AAD `richel@cqclinic.onmicorsoft.com` новым владельцем базы данных с помощью следующей команды:  
    
```    
ALTER AUTHORIZATION ON database::targetDB TO [rachel@cqclinic.onmicrosoft.com];   
```    
    
 Обратите внимание, что имена пользователей Azure AD следует заключать в квадратные скобки.  
  
    
## <a name="see-also"></a>См. также:    
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)     
 [TYPEPROPERTY (Transact-SQL)](../../t-sql/functions/typeproperty-transact-sql.md)     
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)    
 
