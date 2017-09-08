---
title: "ALTER AUTHORIZATION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 31738dcb4eaf4676b4c0a34b13ee400e89333428
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-authorization-transact-sql"></a>ALTER AUTHORIZATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

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
\<class_type > защищаемый класс сущности, для которой изменяется владелец. По умолчанию это класс OBJECT.    
    
|||    
|-|-|    
|OBJECT|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], хранилище данных Azure SQL, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|ASSEMBLY|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ASYMMETRIC KEY|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|AVAILABILITY GROUP |**Область применения**: SQL Server 2012 с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|CERTIFICATE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|CONTRACT|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|DATABASE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION для баз данных](#AlterDB) разделе ниже.|    
|ENDPOINT|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|FULLTEXT CATALOG|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|FULLTEXT STOPLIST|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|MESSAGE TYPE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|REMOTE SERVICE BINDING|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|ROLE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ROUTE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SCHEMA|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], хранилище данных Azure SQL, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|SEARCH PROPERTY LIST|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|SERVER ROLE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SERVICE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SYMMETRIC KEY|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|TYPE|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|XML SCHEMA COLLECTION|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
    
 *имя_сущности*    
 Имя сущности.    
    
 *principal_name* | ВЛАДЕЛЕЦ СХЕМЫ    
 Имя субъекта безопасности, который будет являться собственником сущности.  Объекты базы данных должны принадлежать субъекту базы данных; пользователю базы данных или роли.  Объекты сервера (такие как базы данных) должны принадлежать субъекту сервера (имя для входа). Укажите **владельца СХЕМЫ** как *principal_name* для указания, что объект должен принадлежать участника, который владеет схемой объекта.    
    
## <a name="remarks"></a>Замечания    
 Инструкция ALTER AUTHORIZATION может использоваться для изменения владельца любой сущности, у которой он есть. Владение содержащимися в базе данных сущностями можно передать любому участнику уровня базы данных. Владение сущностями уровня сервера можно передать только участникам уровня сервера.    
    
> [!IMPORTANT]    
>  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], пользователь может владеть объектом (OBJECT) или типом (TYPE), содержащимся в схеме, которая принадлежит другому пользователю базы данных. Это поведение было изменено по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [OBJECTPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/objectproperty-transact-sql.md) и [TYPEPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/typeproperty-transact-sql.md).    
    
 Владение можно передавать для следующих, содержащихся в схемах сущностей типа «объект»: таблиц, представлений, функций, процедур, очередей и синонимов.    
    
 Нельзя передавать владение для следующих сущностей: связанных серверов, статистики, ограничений, правил, значений по умолчанию, триггеров, очередей компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], учетных данных, функций секционирования, схем секционирования, главных ключей баз данных, главного ключа службы, а также для уведомлений о событиях.    
    
 Нельзя передавать владение элементами следующих защищаемых классов: сервером, именем входа, пользователем, ролью приложения и столбцом.    
    
 Аргумент SCHEMA OWNER допустим только в случае передачи владения сущностью, содержащейся в схеме. Аргумент SCHEMA OWNER позволяет передать владение сущностью владельцу схемы, в которой она находится. В схемах содержатся только сущности классов OBJECT, TYPE или XML SCHEMA COLLECTION.    
    
 Если целевая сущность не представляет собой базу данных, а передаваемая сущность передается новому владельцу, все разрешения на целевую сущность удаляются.    
    
> [!CAUTION]    
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] поведение схем отличается от более ранних версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Код, предполагающий, что схемы эквивалентны пользователям базы данных, может возвращать неверные результаты. Старые представления каталога, включая sysobjects, не следует использовать в базе данных, в каком-либо из следующих инструкций DDL инструкций была выполнена: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. В базе данных, в которой когда-либо выполнялась любая из этих инструкций, необходимо использовать новые представления каталога. В новых представлениях каталогов учитывается разделение участников и схем, введенное в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения о представлениях каталогов см. в статье [Представления системных каталогов (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).    
    
 Имейте в виду следующее:    
    
> [!IMPORTANT]    
>  Единственный надежный способ найти владельца объекта является запрос **sys.objects** представления каталога. Единственный надежный способ найти владельца типа — использовать функцию TYPEPROPERTY.    
    
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
  
## <a name="AlterDB"></a>ALTER AUTHORIZATION для баз данных  
**ОБЛАСТЬ ПРИМЕНЕНИЯ**: [!INCLUDE[ssSQL15](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
### <a name="for-sql-server"></a>Для SQL Server:  
**Требования к новому владельцу.**   
Новый владелец участник должен быть одним из следующих:  
-   Имя входа проверки подлинности SQL Server.  
-   Входа проверки подлинности Windows, представляющий пользователя Windows (а не группе).  
-   Пользователь Windows, выполняющем проверку подлинности посредством проверки подлинности имени входа Windows, представляющую собой группу Windows.  
  
**Требования для пользователя, выполняющего инструкцию ALTER AUTHORIZATION:**  
Если вы не являетесь членом **sysadmin** предопределенной роли сервера, необходимо иметь по крайней мере разрешение TAKE OWNERSHIP на базу данных и должен иметь разрешение IMPERSONATE для имени входа нового владельца.   

### <a name="for-azure-sql-database"></a>Для базы данных Azure SQL:  
**Требования к новому владельцу.**   
Новый владелец участник должен быть одним из следующих:  
-   Имя входа проверки подлинности SQL Server.  
-   Федеративный пользователь (не группы) в Azure AD.  
-   Управляемый пользовательский (не группы) или приложения в Azure AD.    

> [!NOTE]  
> Если новый владелец представляет пользователя Azure Active Directory, он не может существовать как пользователь в базе данных, где новый владелец становится новый DBO. Такой пользователь Azure AD необходимо сначала удалить из базы данных перед выполнением инструкции ALTER AUTHORIZATION, Смена владельца базы данных для нового пользователя. Дополнительные сведения о настройке пользователей Azure Active Directory с базой данных SQL см. в разделе [подключение к базе данных SQL или SQL данные хранилища с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
**Требования для пользователя, выполняющего инструкцию ALTER AUTHORIZATION:**  
Необходимо подключиться к целевой базе данных для изменения владельца базы данных.  

Следующие типы учетных записей можно изменить владельца базы данных. 
* Имя входа участника уровня обслуживания. (Администратор SQL Azure подготовлены при создании логического сервера.)  
* Администратор Azure Active Directory для сервера SQL Azure.   
* Текущий владелец базы данных.   
 
  
В следующей таблице перечислены требования:  
  
Исполнитель  |Цель  |Результат    
---------|---------|---------  
Имя входа для проверки подлинности SQL Server     |Имя входа для проверки подлинности SQL Server         |Успешно  
Имя входа для проверки подлинности SQL Server     |Пользователь Azure AD         |Сбой           
Пользователь Azure AD     |Имя входа для проверки подлинности SQL Server         |Успешно           
Пользователь Azure AD     |Пользователь Azure AD         |Успешно           
  
Чтобы проверить Azure AD владельца базы данных, выполните следующую команду Transact-SQL в базе данных пользователя (в этом примере `testdb`).  
    
```    
SELECT CAST(owner_sid as uniqueidentifier) AS Owner_SID   
FROM sys.databases   
WHERE name = 'testdb';  
```    
    
Выход будет иметь идентификатор (например 6D8B81F6-7C79-444C-8858-4AF896C03C67), который соответствует ObjectID Azure AD, назначенные`richel@cqclinic.onmicrosoft.com`  
После проверки подлинности имени входа SQL Server пользователь является владельцем базы данных, выполните следующую инструкцию в базе данных master для проверки владельца базы данных:  
    
```    
SELECT d.name, d.owner_sid, sl.name   
FROM sys.databases AS d  
JOIN sys.sql_logins AS sl  
ON d.owner_sid = sl.sid;  
    
```    
  
### <a name="best-practice"></a>Рекомендации  
  
Вместо использования пользователи Azure AD как отдельные владельцы базы данных используйте группы Azure AD как член **db_owner** предопределенной роли базы данных. Следующие шаги показывают, как настроить отключенное имя входа в качестве владельца базы данных, а группы Azure Active Directory (`mydbogroup`) является членом **db_owner** роли. 
1.  Имя входа для SQL Server, как администратор Azure AD, а также изменение владельца базы данных, отключенное имя входа проверки подлинности SQL Server. Например из пользовательской базы данных выполните следующую команду:  
  ```    
  ALTER AUTHORIZATION ON database::testdb TO DisabledLogin;  
  ```    
2.  Создайте группу Azure AD, который должен быть владельцем базы данных и добавить его в качестве пользователя к пользовательской базе данных. Например:  
  ```    
  CREATE USER [mydbogroup] FROM EXTERNAL PROVIDER;  
  ```    
3.  В пользовательской базе данных добавьте пользователя, представляющий группу Azure AD, с **db_owner** предопределенной роли базы данных. Например:  
  ```    
  ALTER ROLE db_owner ADD MEMBER mydbogroup;  
  ```    
  
Теперь `mydbogroup` члены можно централизованно управлять базы данных как члены **db_owner** роли.  
- Когда члены этой группы удаляются из группы Azure AD, они автоматически отменив dbo разрешения для этой базы данных.  
- Аналогичным образом при добавлении новых членов к `mydbogroup` группы Azure AD, он автоматически получает доступ dbo для этой базы данных.  
  
Проверка наличия определенного пользователя dbo действующие разрешения, пользователь должен выполнить следующую инструкцию:  
    
```    
SELECT IS_MEMBER ('db_owner');  
```    
  
Возвращаемое значение 1 указывает, что пользователь является членом роли.  
   
    
## <a name="permissions"></a>Permissions    
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
    
 Если объекты схемы не включены в инструкцию, [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполнит поиск объекта в схеме по умолчанию пользователи. Например:    
    
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
    
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].    
    
```    
ALTER AUTHORIZATION ON ENDPOINT::CantabSalesServer1 TO JaePak;    
GO    
```    
    
### <a name="e-changing-the-owner-of-a-table"></a>Д. Изменение владельца таблицы    
 В каждом из следующих примеров изменяет владельца `Sprockets` в таблицу `Parts` базы данных с пользователем базы данных `MichikoOsada`.    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON dbo.Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::dbo.Sprockets TO MichikoOsada;    
```    
    
### <a name="f-changing-the-owner-of-a-database"></a>Е. Изменение владельца базы данных    
 **Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].    
    
 Следующий пример изменить владельца `Parts` базы данных с именем входа `MichikoOsada`.    
    
```    
ALTER AUTHORIZATION ON DATABASE::Parts TO MichikoOsada;    
```    
  
### <a name="g-changing-the-owner-of-a-sql-database-to-an-azure-ad-user"></a>Ж. Изменение владельца базы данных SQL для пользователя Azure AD  
В следующем примере, администратор Azure Active Directory для SQL Server в организации с active directory, с именем `cqclinic.onmicrosoft.com`, можно изменить текущую принадлежность базы данных `targetDB` и сделать пользователя AAD `richel@cqclinic.onmicorsoft.com` новой базы данных Владелец, используя следующую команду:  
    
```    
ALTER AUTHORIZATION ON database::targetDB TO [rachel@cqclinic.onmicrosoft.com];   
```    
    
 Обратите внимание, что для пользователей Azure AD квадратные скобки имя пользователя необходимо использовать.  
  
    
## <a name="see-also"></a>См. также:    
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)     
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)     
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)    
 

