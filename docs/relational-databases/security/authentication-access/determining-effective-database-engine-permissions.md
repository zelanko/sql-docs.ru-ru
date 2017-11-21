---
title: "Определение действующих разрешений для ядра СУБД | Документация Майкрософт"
ms.custom: 
ms.date: 01/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions, effective
- effective permissions
ms.assetid: 273ea09d-60ee-47f5-8828-8bdc7a3c3529
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d21efb4495f786b6000fe0b8675fa042b4d2ca6e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="determining-effective-database-engine-permissions"></a>Определение действующих разрешений для ядра СУБД
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Здесь описывается, как определить, кто имеет разрешения на различные объекты в ядре СУБД SQL Server. SQL Server реализует две системы разрешений для ядра СУБД. Более старая система предопределенных ролей имеет предварительно настроенные разрешения. Начиная с версии SQL Server 2005, доступна более гибкая и точная система. (Сведения из данного раздела также относятся к службам SQL Server, начиная с версии 2005. Отдельные типы разрешений недоступны в некоторых версиях SQL Server.)

>  [!IMPORTANT] 
>  * Действующие разрешения — это совокупность обеих систем разрешений. 
>  * Отклонение разрешений переопределяет их предоставление. 
>  * Если пользователь является участником предопределенной роли сервера системного администратора, разрешения не проверяются, поэтому отклонения не применяются. 
>  * Старая и новая системы имеют сходства. Например, участие в предопределенной роли сервера `sysadmin` похоже на наличие разрешений `CONTROL SERVER`. Однако эти системы не идентичны. Например, если имя входа имеет только разрешение `CONTROL SERVER` и хранимая процедура проверяет на членство в предопределенной роли сервера `sysadmin`, то произойдет сбой проверки разрешения. То же самое будет наблюдаться и в обратной ситуации. 


## <a name="summary"></a>Сводка   
* Разрешения уровня сервера могут исходить из членства в предопределенной роли сервера или пользовательских серверных ролях. Все пользователи принадлежат к предопределенной роли сервера `public` и получают назначенные ей разрешения.   
* Разрешения уровня сервера могут исходить из разрешений, предоставленных имени входа или серверным ролям, определяемым пользователем.   
* Разрешения уровня базы данных могут исходить из членства в предопределенных ролях базы данных или в определяемых пользователем ролях базы данных в каждой базе данных. Все пользователи принадлежат к предопределенной роли базы данных `public` и получают назначенные ей разрешения.   
* Разрешения уровня базы данных могут исходить из разрешений, предоставленных пользователям или пользовательским ролям базы данных в каждой базе данных.   
* Разрешения могут быть получены от имени входа `guest` или пользователя базы данных `guest`, если он включен. Имя входа `guest` и пользователи по умолчанию отключены.   
* Пользователи Windows могут быть участниками групп Windows, которые могут иметь имена входа. SQL Server узнает о членстве в группе Windows, когда пользователь Windows подключается и предоставляет токен Windows с идентификатором безопасности группы Windows. Так как SQL Server не контролирует и не получает автоматические обновления участия в группах Windows, SQL Server не может определенно сообщить о разрешениях пользователей Windows, полученных от членства в группе Windows.   
* Разрешения можно получить, переключившись на роль приложения и предоставив пароль.   
* Разрешения можно получить, выполнив хранимую процедуру, которая включает в себя предложение `EXECUTE AS`.   
* Разрешения можно получить от имен входа и пользователей с помощью разрешения `IMPERSONATE`.   
* Участники группы администраторов локальных компьютеров всегда могут повышать свои права доступа до `sysadmin`. (Не относится к базе данных SQL.)  
* Участники предопределенной роли сервера `securityadmin` могут повысить многие права и в некоторых случаях могут повысить уровень привилегий до `sysadmin`. (Не относится к базе данных SQL.)   
* Администраторы SQL Server могут просматривать сведения обо всех именах входа и пользователях. Пользователи с меньшими полномочиями обычно видят сведения только о собственных идентификаторах.

## <a name="older-fixed-role-permission-system"></a>Более старая система разрешений предопределенной роли

Для предопределенных ролей сервера и предопределенных ролей базы данных предварительно настроены разрешения, которые не могут быть изменены. Чтобы определить, кто является участником предопределенной роли сервера, выполните следующий запрос.    
>  [!NOTE] 
>  Не относится к базе данных SQL или хранилищу данных SQL, где разрешение на уровне сервера недоступно. Столбец `is_fixed_role` таблицы `sys.server_principals` был добавлен в SQL Server 2012. Он не требуется для более старых версий SQL Server.  
```tsql
SELECT SP1.name AS ServerRoleName, 
 isnull (SP2.name, 'No members') AS LoginName   
 FROM sys.server_role_members AS SRM
 RIGHT OUTER JOIN sys.server_principals AS SP1
   ON SRM.role_principal_id = SP1.principal_id
 LEFT OUTER JOIN sys.server_principals AS SP2
   ON SRM.member_principal_id = SP2.principal_id
 WHERE SP1.is_fixed_role = 1 -- Remove for SQL Server 2008
 ORDER BY SP1.name;
```
>  [!NOTE] 
>  * Все имена входа являются участниками общей роли, и их нельзя удалить. 
>  * Этот запрос проверяет таблицы в базе данных master, но может выполняться в любой базе данных локального продукта. 

Чтобы определить, кто является участником предопределенной роли базы данных, выполните следующий запрос в каждой базе данных.
```tsql
SELECT DP1.name AS DatabaseRoleName, 
   isnull (DP2.name, 'No members') AS DatabaseUserName 
 FROM sys.database_role_members AS DRM
 RIGHT OUTER JOIN sys.database_principals AS DP1
   ON DRM.role_principal_id = DP1.principal_id
 LEFT OUTER JOIN sys.database_principals AS DP2
   ON DRM.member_principal_id = DP2.principal_id
 WHERE DP1.is_fixed_role = 1
 ORDER BY DP1.name;
```
Чтобы понять разрешения, предоставляемые каждой роли, см. описания роли на иллюстрациях в электронной документации (о [ролях уровня сервера](../../../relational-databases/security/authentication-access/server-level-roles.md) и [ролях уровня базы данных](../../../relational-databases/security/authentication-access/database-level-roles.md)).

## <a name="newer-granular-permission-system"></a>Новая система детализированных разрешений

Эта система чрезвычайно гибкая, но она может стать достаточно сложной, если настроить права более точно. Это не всегда приводит к плохим результатам. Например, в финансовом учреждении требуется точная настройка. Чтобы упростить работу, система позволяет создавать роли, назначать разрешения ролям, а затем добавлять группы пользователей в роли. В идеале команда разработки базы данных может разделить действия в виде схемы, а затем предоставить разрешения роли всей схеме, а не отдельным таблицам или процедурам. В реальности все сложнее, так как организациям зачастую требуется создавать непредвиденные требования к безопасности.   

На следующей схеме показаны разрешения и их связи друг с другом. Некоторые из разрешений более высокого уровня (например, `CONTROL SERVER`) указаны несколько раз. Рисунок в этой статье слишком мал для чтения. Щелкните изображение, чтобы скачать **плакат разрешений для ядра СУБД** в формате PDF.  
  
 [![Разрешения для ядра СУБД](../../../relational-databases/security/media/database-engine-permissions.PNG)](http://go.microsoft.com/fwlink/?LinkId=229142)

### <a name="security-classes"></a>Классы безопасности

Разрешения могут быть предоставлены на уровне сервера, на уровне базы данных, на уровне схемы или на уровне объекта и т. д. Существует 26 уровней (они называются классами). Полный список классов в алфавитном порядке выглядит следующим образом: `APPLICATION ROLE`, `ASSEMBLY`, `ASYMMETRIC KEY`, `AVAILABILITY GROUP`, `CERTIFICATE`, `CONTRACT`, `DATABASE`, `DATABASE` `SCOPED CREDENTIAL`, `ENDPOINT`, `FULLTEXT CATALOG`, `FULLTEXT STOPLIST`, `LOGIN`, `MESSAGE TYPE`, `OBJECT`, `REMOTE SERVICE BINDING`, `ROLE`, `ROUTE`, `SCHEMA`, `SEARCH PROPERTY LIST`, `SERVER`, `SERVER ROLE`, `SERVICE`, `SYMMETRIC KEY`, `TYPE`, `USER`, `XML SCHEMA COLLECTION`. (Некоторые классы недоступны для определенных типов серверов SQL Server.) Для предоставления полных сведений о каждом классе требуется отдельный запрос.

### <a name="principals"></a>Субъекты

Разрешения предоставляются субъектам. Субъектами могут быть серверные роли, имена входа, роли базы данных или пользователи. Имена входа могут представлять группы Windows, которые содержат множество пользователей Windows. Так как SQL Server не управляет группами Windows, он не всегда знает, кто является участником группы Windows. Когда пользователь Windows подключается к SQL Server, пакет входа содержит токены членства в группе Windows для пользователя.

При подключении пользователя Windows с помощью имени входа на основе группы Windows для некоторых действий серверу SQL Server потребуется создать имя входа или пользователя для олицетворения отдельного пользователя Windows. Например, группа Windows ("Инженеры") содержит пользователей (Мария, Тимофей, Григорий), и у этой группы есть учетная запись пользователя базы данных. Если Мария имеет разрешение и создает таблицу, можно создать пользователя (Mariya) в качестве владельца таблицы. Если для Тимофея отклонено разрешение, которое имеют остальные участники группы "Инженеры", необходимо создать соответствующего пользователя, чтобы отследить отклонение разрешения.

Помните, что пользователь Windows может быть участником нескольких групп Windows (например, "Инженеры" и "Менеджеры"). Разрешения, предоставленные или отклоненные для имени входа "Инженеры" или "Менеджеры", индивидуально для каждого пользователя или для ролей, участником которых является пользователь, будут объединены и оценены для определения действующих разрешений. Функция `HAS_PERMS_BY_NAME` выявляет наличие определенного разрешения у пользователя или имени входа. Тем не менее невозможно определить источник предоставления или отклонения разрешения. Необходимо изучить список разрешений и попробовать их на практике.

## <a name="useful-queries"></a>Полезные запросы

### <a name="server-permissions"></a>Разрешения сервера

Следующий запрос возвращает список разрешений, которые были предоставлены или запрещены на уровне сервера. Этот запрос должен быть выполнен в базе данных master.   
>  [!NOTE] 
>  Разрешения уровня сервера нельзя предоставлять и запрашивать в базе данных SQL или в хранилище данных SQL.   
```tsql
SELECT pr.type_desc, pr.name, 
 isnull (pe.state_desc, 'No permission statements') AS state_desc, 
 isnull (pe.permission_name, 'No permission statements') AS permission_name 
 FROM sys.server_principals AS pr
 LEFT OUTER JOIN sys.server_permissions AS pe
   ON pr.principal_id = pe.grantee_principal_id
 WHERE is_fixed_role = 0 -- Remove for SQL Server 2008
 ORDER BY pr.name, type_desc;
```

### <a name="database-permissions"></a>Разрешения базы данных

Следующий запрос возвращает список разрешений, которые были предоставлены или отклонены на уровне базы данных. Этот запрос должен быть выполнен в каждой базе данных.   
```tsql
SELECT pr.type_desc, pr.name, 
 isnull (pe.state_desc, 'No permission statements') AS state_desc, 
 isnull (pe.permission_name, 'No permission statements') AS permission_name 
FROM sys.database_principals AS pr
LEFT OUTER JOIN sys.database_permissions AS pe
    ON pr.principal_id = pe.grantee_principal_id
WHERE pr.is_fixed_role = 0 
ORDER BY pr.name, type_desc;
```

Каждый класс разрешений в таблице разрешений может быть присоединен к другим системным представлениям, содержащим связанные сведения о классе защищаемого объекта. Например, следующий запрос предоставляет имя объекта базы данных, на которого распространяется разрешение.    
```tsql
SELECT pr.type_desc, pr.name, pe.state_desc, 
 pe.permission_name, s.name + '.' + oj.name AS Object, major_id
 FROM sys.database_principals AS pr
 JOIN sys.database_permissions AS pe
   ON pr.principal_id = pe.grantee_principal_id
 JOIN sys.objects AS oj
   ON oj.object_id = pe.major_id
 JOIN sys.schemas AS s
   ON oj.schema_id = s.schema_id
 WHERE class_desc = 'OBJECT_OR_COLUMN';
```
Используйте функцию `HAS_PERMS_BY_NAME`, чтобы определить, имеет ли разрешение конкретный пользователь (в данном случае `TestUser`). Например:   
```tsql
EXECUTE AS USER = 'TestUser';
SELECT HAS_PERMS_BY_NAME ('dbo.T1', 'OBJECT', 'SELECT');
REVERT;
```
Сведения о синтаксисе см. в статье [HAS_PERMS_BY_NAME](../../../t-sql/functions/has-perms-by-name-transact-sql.md).

## <a name="see-also"></a>См. также:

[Приступая к работе с разрешениями ядра СУБД](../../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)    
[Руководство по началу работы с ядром СУБД](Tutorial:%20Getting%20Started%20with%20the%20Database%20Engine.md) 


