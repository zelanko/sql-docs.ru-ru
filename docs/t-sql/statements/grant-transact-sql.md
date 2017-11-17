---
title: "GRANT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GRANT_TSQL
- GRANT
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], GRANT statement
- schema-level securables [SQL Server]
- GRANT statement
- cross-database permissions
- GRANT statement, about GRANT statement
- server-level securables [SQL Server]
- database-level securables [SQL Server]
- permissions [SQL Server], granting
ms.assetid: a760c16a-4d2d-43f2-be81-ae9315f38185
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bb9bf548f042a4a6f41322fb789a2cd7e5b6bec9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grant-transact-sql"></a>Инструкция GRANT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Предоставляет разрешения на защищаемый объект участнику.  Общий подход заключается в том, чтобы ПРЕДОСТАВИТЬ \<некоторые разрешения > ON \<некоторый объект > TO \<некоторые пользователя, имя входа или группы >. Общее описание разрешений см. в разделе [разрешения &#40; компонент Database Engine &#41;](../../relational-databases/security/permissions-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for GRANT  
GRANT { ALL [ PRIVILEGES ] }  
      | permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      [ ON [ class :: ] securable ] TO principal [ ,...n ]   
      [ WITH GRANT OPTION ] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class_type> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 ALL  
 Этот параметр устарел и сохранен только для поддержки обратной совместимости. Он не предоставляет все возможные разрешения. Выдача разрешения ALL эквивалентна предоставлению следующих разрешений.  
  
-   Если защищаемым объектом является база данных, аргумент ALL относится к разрешениям BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE и CREATE VIEW.  
  
-   Если защищаемым объектом является скалярная функция, аргумент ALL относится к разрешениям EXECUTE и REFERENCES.  
  
-   Если защищаемым объектом является функция с табличным значением, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
-   Если защищаемая сущность является хранимой процедурой, аргумент ALL подразумевает разрешение EXECUTE.  
  
-   Если защищаемым объектом является таблица, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
-   Если защищаемым объектом является представление, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
PRIVILEGES  
 Включено для обеспечения совместимости с требованиями ISO. Не изменяет работу ALL.  
  
*разрешение*  
 Имя разрешения. Допустимые сопоставления разрешений защищаемых объектов описаны в разделах, перечисленных ниже.  
  
*столбец*  
 Указывает имя столбца таблицы, на который предоставляется разрешение. Необходимы скобки ().  
  
*класс*  
 Указывает класс защищаемого объекта, для которого предоставляется разрешение. Квалификатор области **::** является обязательным.  
  
*защищаемый объект*  
 Указывает защищаемый объект, на который предоставляется разрешение.  
  
Чтобы *участника*  
 Имя участника. Состав участников, которым можно предоставлять разрешения, меняется в зависимости от защищаемого объекта. Допустимые сочетания описаны в разделах, перечисленных ниже.  
  
GRANT OPTION  
 Показывает, что получающему разрешению будет также дана возможность предоставлять указанное разрешение другим участникам.  
  
AS *участника*  
 Используйте основной AS, чтобы указать, что участника записываются как предоставил разрешение должно быть участником, отличных от пользователя, выполняющего инструкцию. Предположим, что пользователь Mary является principal_id 12, и пользователь Raul является основной 15. Мария выполняет `GRANT SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;` теперь в таблице sys.database_permissions покажет, что grantor_prinicpal_id было 15 (Raul), несмотря на то, что инструкция была фактически выполнена пользователем 13 (Mary).

С помощью предложения AS обычно не рекомендуется, если вам нужно явно определять цепочки разрешение. Дополнительные сведения см. в разделе **Сводка по алгоритму проверки разрешений** раздел [разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md).

Использование этой инструкции не предусматривает возможность олицетворять другого пользователя. 
  
## <a name="remarks"></a>Замечания  
 Полное описание синтаксиса инструкции GRANT сложно. Предыдущая диаграмма синтаксиса была упрощена, чтобы продемонстрировать ее структуру. Полное описание синтаксиса предоставления разрешений на конкретные защищаемые объекты приведено в разделах, перечисленных ниже.  
  
 Инструкция REVOKE может использоваться для удаления уже выданных прав доступа, а инструкция DENY может использоваться, чтобы предотвратить получение участником определенного разрешения посредством инструкции GRANT.  
  
 Предоставление разрешения удаляет DENY или REVOKE для этого разрешения на данный защищаемый объект. Если то же разрешение запрещено для более высокой области действия, которая содержит данный защищаемый объект, то DENY имеет более высокий приоритет. Но отмена разрешения, выданного в более высокой области действия, не получает такого приоритета.  
  
 Разрешения уровня базы данных выдаются в пределах области указанной базы данных. Если пользователю нужны разрешения на объекты в другой базе данных, необходимо создать для него учетную запись в этой базе данных или предоставить ему разрешение на доступ как к текущей, так и к другим базам данных.  
  
> [!CAUTION]  
>  Запрет (DENY) уровня таблицы имеет меньший приоритет, чем разрешение (GRANT) уровня столбца. Эта несовместимость в иерархии разрешений предусмотрена в целях гарантии обратной совместимости. В будущем выпуске она будет удалена.  
  
 Системная хранимая процедура sp_helprotect сообщает о разрешениях на доступ к защищаемым объектам уровня базы данных.  
  
## <a name="with-grant-option"></a>WITH GRANT OPTION  
 **GRANT** ... **С параметром GRANT OPTION** указывает, что получающему разрешение субъекту безопасности предоставлена возможность предоставлять указанное разрешение другим учетным записям безопасности. Если участник, получивший данное разрешение роли или группы Windows, **AS** предложения необходимо использовать, когда требуется разрешение объекта для последующего предоставления пользователям, которые не являются членами группы или роли. Поскольку может выполнять только пользователь, а не группа или роль, **GRANT** необходимо использовать инструкцию, членом определенной группы или роли **AS** предложение для явного вызова членства роли или группы при предоставлении разрешение. В следующем примере показан способ **WITH GRANT OPTION** используется при предоставлении роли или группе Windows.  
  
```  
-- Execute the following as a database owner  
GRANT EXECUTE ON TestProc TO TesterRole WITH GRANT OPTION;  
EXEC sp_addrolemember TesterRole, User1;  
-- Execute the following as User1  
-- The following fails because User1 does not have the permission as the User1  
GRANT EXECUTE ON TestMe TO User2;  
-- The following succeeds because User1 invokes the TesterRole membership  
GRANT EXECUTE ON TestMe TO User2 AS TesterRole;  
```  
  
## <a name="chart-of-sql-server-permissions"></a>Диаграмма разрешений SQL Server  
 Схему плакатного размера всех разрешений компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в формате PDF см. по ссылке [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## <a name="permissions"></a>Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое. Если используется параметр AS, налагаются дополнительные ограничения. Дополнительные сведения см. в разделах, посвященных конкретным защищаемым объектам.  
  
 Владельцы объектов могут предоставлять разрешения на объекты, которыми они владеют. Участники, имеющие разрешение CONTROL на защищаемый объект, могут предоставлять разрешение на этот защищаемый объект.  
  
 Участники, которым предоставлено разрешение CONTROL SERVER, такие как члены предопределенной роли сервера &lt;legacyBold&gt;sysadmin&lt;/legacyBold&gt;, могут предоставлять любое разрешение на любой защищаемый объект сервера. Участники, получившие разрешение CONTROL на базу данных, такие как члены предопределенной роли базы данных db_owner, могут предоставлять любое разрешение на любой защищаемый объект в базе данных. Владельцы разрешения CONTROL, связанного со схемой, могут предоставлять любые разрешения на работу с любыми объектами, содержащимися в данной схеме.  
  
## <a name="examples"></a>Примеры  
 В следующей таблице перечислены защищаемые объекты и разделы, в которых описывается синтаксис инструкций по работе с ними.  
  
|||  
|-|-|  
|Роль приложения|[Предоставление разрешений участникам базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Сборка|[ПРЕДОСТАВЬТЕ разрешения для сборки &#40; Transact-SQL &#41;](../../t-sql/statements/grant-assembly-permissions-transact-sql.md)|  
|Асимметричный ключ|[Предоставление разрешений на асимметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/grant-asymmetric-key-permissions-transact-sql.md)|  
|Группа доступности|[Группа доступности ПРЕДОСТАВЬТЕ разрешения &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)|  
|Сертификат|[Разрешения GRANT сертификатов &#40; Transact-SQL &#41;](../../t-sql/statements/grant-certificate-permissions-transact-sql.md)|  
|Контракт|[Разрешения GRANT службы Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|База данных|[ПРЕДОСТАВИТЬ разрешения базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)|
|Учетные данные области базы данных|[В области базы данных GRANT учетных данных (Transact-SQL)](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)|  
|Конечная точка|[Предоставление разрешений на конечные точки &#40; Transact-SQL &#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)|  
|Полнотекстовый каталог|[Разрешения GRANT Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|Полнотекстовый список стоп-слов|[Разрешения GRANT Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|Функция|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Имя входа|[Предоставление разрешений участникам Server &#40; Transact-SQL &#41;](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)|  
|Тип сообщений|[Разрешения GRANT службы Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Объект|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Очередь|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Привязка удаленной службы|[Разрешения GRANT службы Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Роль|[Предоставление разрешений участникам базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Маршрут|[Разрешения GRANT службы Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|схема|[GRANT разрешения схемы &#40; Transact-SQL &#41;](../../t-sql/statements/grant-schema-permissions-transact-sql.md)|  
|Список свойств поиска|[Разрешения списка свойств поиска GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)|  
|Server|[GRANT, предоставление разрешений на сервер (Transact-SQL)](../../t-sql/statements/grant-server-permissions-transact-sql.md)|  
|Служба|[Разрешения GRANT службы Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Хранимая процедура|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Симметричный ключ|[ПРЕДОСТАВЬТЕ разрешения на симметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)|  
|Синоним|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Системные объекты|[GRANT, предоставление разрешения на системный объект (Transact-SQL)](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)|  
|Таблица|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Тип|[Разрешения типа GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)|  
|Пользователь|[Предоставление разрешений участникам базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Просмотр|[Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Коллекция схем XML|[ПРЕДОСТАВЬТЕ разрешения на коллекцию схем XML &#40; Transact-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>См. также:  
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

