---
title: "DENY, разрешения объекта (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- DENY statement, objects
- table permissions [SQL Server]
ms.assetid: 0b8d3ddc-38c0-4241-b7bb-ee654a5081aa
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dc405b480d063ff6990182f9a66cc6f4e35c3a5a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="deny-object-permissions-transact-sql"></a>DENY, запрет разрешений на объект (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения на член класса OBJECT защищаемых объектов. Элементы класса OBJECT: таблицы, представления, функции с табличным значением, хранимые процедуры, расширенные хранимые процедуры, скалярные функции, агрегатные функции, очереди обслуживания и синонимы.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        TO <database_principal> [ ,...n ]   
    [ CASCADE ]  
        [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Обозначает разрешение, которое можно запретить для содержащегося в схеме объекта. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 ALL  
 Запрет разрешения ALL не запрещает все возможные разрешения. Запрет ALL эквивалентен запрету всех разрешений ANSI-92, применимых к данному объекту. Значение ALL различается для разных типов объектов  
  
 - Разрешения на скалярные функции: выполнение, ссылается на.  
 - Табличная функция разрешения: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
 - Разрешения на хранимые процедуры: выполнение.  
 - Таблица разрешения: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
 - Просмотр разрешений: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
PRIVILEGES  
 Включено для совместимости с ANSI-92. Не изменяет работу ALL.  
  
*столбец*  
 Указывает имя столбца в таблице, представлении или функции с табличным значением, для которых запрещается разрешение. Круглые скобки **()** являются обязательными. Для столбца можно запрещать только разрешения SELECT, REFERENCES и UPDATE. *столбец* может быть указан в предложении permissions или после имени защищаемого объекта.  
  
> [!CAUTION]  
>  Запрет (DENY) уровня таблицы имеет меньший приоритет, чем разрешение (GRANT) уровня столбца. Такая несогласованность в иерархии разрешений сохранена в целях обратной совместимости.  
  
 ON [объект **::** ] [ *имя_схемы* ] **.** *object_name*  
 Указывает объект, для которого запрещается разрешение. Фраза OBJECT необязательна Если *schema_name* указано. Если ЖЕ она указана, указание квалификатора области (**::**) является обязательным. Если *schema_name* не указан, используется схема по умолчанию. Если *имя_схемы* указана, указание квалификатора области схемы (**.**) является обязательным.  
  
 Чтобы \<database_principal >  
 Задает участника, для которого запрещается разрешение, —  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS \<database_principal >  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Сведения об объектах доступны через различные представления каталога. Дополнительные сведения см. в разделе [представления каталога объектов &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 Объект является защищаемым на уровне схемы. Он содержится в схеме, которая является его родителем в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить для объекта, перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение объекта|Содержится в разрешении объекта|Содержится в разрешении схемы|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|DELETE|CONTROL|DELETE|  
|Выполните|CONTROL|Выполните|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL для данного объекта.  
  
 При использовании предложения AS указанный участник должен быть владельцем объекта, разрешения на который запрещаются для этого участника.  
  
## <a name="examples"></a>Примеры  
В следующих примерах используется база данных AdventureWorks.
  
### <a name="a-denying-select-permission-on-a-table"></a>A. Запрет разрешения SELECT на таблицу  
 В следующем примере запрещается `SELECT` разрешение пользователю `RosaQdM` в таблице `Person.Address`.  
  
```  
DENY SELECT ON OBJECT::Person.Address TO RosaQdM;  
GO  
```  
  
### <a name="b-denying-execute-permission-on-a-stored-procedure"></a>Б. Запрет разрешения EXECUTE на хранимую процедуру  
 В следующем примере запрещается разрешение `EXECUTE` на хранимую процедуру `HumanResources.uspUpdateEmployeeHireInfo` для роли приложения под названием `Recruiting11`.  
  
```  
DENY EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO   
```  
  
### <a name="c-denying-references-permission-on-a-view-with-cascade"></a>В. Запрет разрешения REFERENCES на представление с CASCADE  
 В следующем примере запрещается разрешение `REFERENCES` на столбец `BusinessEntityID` в представлении `HumanResources.vEmployee` для пользователя `Wanida` с `CASCADE`.  
  
```  
DENY REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    TO Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)   
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  
