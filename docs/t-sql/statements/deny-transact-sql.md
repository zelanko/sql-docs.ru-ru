---
title: "DENY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/15/2017
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
- DENY
- DENY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- security [SQL Server], denying access
- DENY statement
- permissions [SQL Server], denying
- server-level securables [SQL Server]
- inherited security settings [SQL Server]
- denying permissions [SQL Server], DENY statement
- principal security [SQL Server]
- database-level securables [SQL Server]
- denying permissions [SQL Server]
ms.assetid: c32d1e01-9ee9-4665-a516-fcfece58078e
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 08f2d3c555dceef71e331b6df8727afb5780b86b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-transact-sql"></a>DENY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Запрещает разрешение для участника. Предотвращает наследование разрешения участником через его членство в группе или роли. DENY имеет приоритет над всеми разрешениями, за исключением того, чтобы запретить не применяется к владельцы объектов или члены фиксированной серверной роли sysadmin.
  **Примечание по безопасности** члены предопределенной роли сервера и владельцы объектов не может быть отказано в разрешениях.»
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for DENY  
DENY   { ALL [ PRIVILEGES ] } 
     | <permission>  [ ( column [ ,...n ] ) ] [ ,...n ]  
    [ ON [ <class> :: ] securable ] 
    TO principal [ ,...n ]   
    [ CASCADE] [ AS principal ]  
[;]

<permission> ::=  
{ see the tables below }  
  
<class> ::=  
{ see the tables below }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class> ::=  
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
 Этот параметр запрещает не все возможные разрешения. Его использование эквивалентно запрету следующих разрешений.  
  
-   Если защищаемым объектом является база данных, аргумент ALL относится к разрешениям BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE и CREATE VIEW.  
  
-   Если защищаемым объектом является скалярная функция, аргумент ALL относится к разрешениям EXECUTE и REFERENCES.  
  
-   Если защищаемым объектом является функция с табличным значением, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
-   Если защищаемая сущность является хранимой процедурой, аргумент ALL подразумевает разрешение EXECUTE.  
  
-   Если защищаемым объектом является таблица, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
-   Если защищаемым объектом является представление, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
> [!NOTE]  
>  Синтаксис DENY ALL является устаревшим. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого отменяйте определенные разрешения.  
  
 PRIVILEGES  
 Включено для обеспечения совместимости с требованиями ISO. Не изменяет работу ALL.  
  
 *разрешение*  
 Имя разрешения. Допустимые сопоставления разрешений защищаемых объектов описаны в разделах, перечисленных ниже.  
  
 *столбец*  
 Указывает имя столбца в таблице, на который запрещаются разрешения. Необходимы скобки ().  
  
 *класс*  
 Указывает класс защищаемого объекта, на который запрещается разрешение. Квалификатор области **::** является обязательным.  
  
 *защищаемый объект*  
 Указывает защищаемый объект, на который запрещается разрешение.  
  
 Чтобы *участника*  
 Имя участника. Участники, у которых может запрещаться разрешение на защищаемый объект, в зависимости от самого защищаемого объекта. Допустимые сочетания приведены в указанных ниже разделах по конкретным защищаемым объектам.  
  
 CASCADE  
 Обозначает, что разрешение запрещается для указанного участника и всех других участников, которым этот участник предоставил разрешение. Требуется, если участник имеет разрешение с параметром GRANT OPTION.  
  
 AS *участника*  
  Используйте предложение AS участника для указания, что участник, зарегистрированным как denier разрешения должны быть участником, отличных от пользователя, выполняющего инструкцию. Предположим, что пользователь Mary является principal_id 12, и пользователь Raul является основной 15. Мария выполняет `DENY SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;` теперь в таблице sys.database_permissions покажет, что grantor_prinicpal_id инструкции deny не 15 (Raul), несмотря на то, что инструкция была фактически выполнена пользователем 13 (Mary).
  
Использование этой инструкции не предусматривает возможность олицетворять другого пользователя.  
  
## <a name="remarks"></a>Замечания  
 Полный синтаксис инструкции DENY достаточно сложен. Предыдущая диаграмма синтаксиса была упрощена, чтобы продемонстрировать ее структуру. Полный синтаксис запрета разрешений на конкретные защищаемые объекты описан в разделах, перечисленных ниже.  
  
 Инструкция DENY завершится ошибкой, если не указан аргумент CASCADE при отзыве разрешения у участника, которому это разрешение было предоставлено с параметром GRANT OPTION.  
  
 Системная хранимая процедура sp_helprotect сообщает о разрешениях на доступ к защищаемым объектам уровня базы данных.  
  
> [!CAUTION]  
>  Запрет (DENY) уровня таблицы имеет меньший приоритет, чем разрешение (GRANT) уровня столбца. Эта несовместимость в иерархии разрешений предусмотрена в целях гарантии обратной совместимости. В будущем выпуске она будет удалена.  
  
> [!CAUTION]  
>  При запрете разрешения CONTROL на базу данных неявно запрещается разрешение CONNECT на эту базу данных. Участник, для которого запрещено разрешение CONTROL на базу данных, не сможет подключиться к этой базе данных.  
  
> [!CAUTION]  
>  При запрете разрешения CONTROL SERVER неявно запрещается разрешение CONNECT SQL на этот сервер. Участник, для которого запрещено разрешение CONTROL SERVER на сервер, не сможет подключиться к этому серверу.  
  
## <a name="permissions"></a>Permissions  
 Участник, указанный параметром AS, должен иметь либо разрешение CONTROL, либо разрешение более высокого уровня, включающее в себя разрешение на защищаемый объект. При использовании параметра AS указанный участник должен быть владельцем защищаемого объекта, разрешение на который запрещается.  
  
 Участник, получивший разрешение CONTROL SERVER, например член предопределенной роли сервера sysadmin, может запретить любое разрешение на любой защищаемый объект сервера. Участник, получивший разрешение CONTROL на базу данных, например член предопределенной роли базы данных db_owner, может запретить любое разрешение на любой защищаемый объект в базе данных. Участник, получивший разрешение CONTROL на схему, может запретить любое разрешение на любой защищаемый объект в этой схеме. При использовании предложения AS указанный участник должен быть владельцем защищаемого объекта, разрешения на который для него запрещаются.  
  
## <a name="examples"></a>Примеры  
 В следующей таблице перечислены защищаемые объекты и разделы, в которых описывается синтаксис инструкций по работе с ними.  
  
|||  
|-|-|  
|Роль приложения|[Запрет разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Сборка|[ЗАПРЕТИТЬ разрешения для сборки &#40; Transact-SQL &#41;](../../t-sql/statements/deny-assembly-permissions-transact-sql.md)|  
|Асимметричный ключ|[ЗАПРЕТ разрешений на асимметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/deny-asymmetric-key-permissions-transact-sql.md)|  
|Группа доступности|[ЗАПРЕТ разрешений группы доступности &#40; Transact-SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)|  
|Сертификат|[ЗАПРЕТ разрешений на сертификат &#40; Transact-SQL &#41;](../../t-sql/statements/deny-certificate-permissions-transact-sql.md)|  
|Контракт|[ЗАПРЕТ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|База данных|[Запрет разрешения базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-permissions-transact-sql.md)|  
|Учетные данные области базы данных|[ЗАПРЕЩАЮЩИЕ области базы данных учетных данных (Transact-SQL)](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)|  
|Конечная точка|[ЗАПРЕТ разрешений на конечные точки &#40; Transact-SQL &#41;](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)|  
|Полнотекстовый каталог|[Запрет разрешения Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|Полнотекстовый список стоп-слов|[Запрет разрешения Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|Функция|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Имя входа|[Запрет разрешения участника на уровне сервера &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)|  
|Тип сообщений|[ЗАПРЕТ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Объект|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Очередь|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Привязка удаленной службы|[ЗАПРЕТ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Роль|[Запрет разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Маршрут|[ЗАПРЕТ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|схема|[Запрет разрешения схемы &#40; Transact-SQL &#41;](../../t-sql/statements/deny-schema-permissions-transact-sql.md)|  
|Список свойств поиска|[Запрет разрешения Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/deny-search-property-list-permissions-transact-sql.md)|  
|Server|[Запрет разрешения Server &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-permissions-transact-sql.md)|  
|Служба|[ЗАПРЕТ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Хранимая процедура|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Симметричный ключ|[Запрет разрешения на симметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)|  
|Синоним|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Системные объекты|[ЗАПРЕТ разрешений на системные объекты &#40; Transact-SQL &#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)|  
|Таблица|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Тип|[Запрет разрешения типа &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)|  
|Пользователь|[Запрет разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Просмотр|[ЗАПРЕТ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Коллекция схем XML|[Запрет разрешения на коллекцию схем XML &#40; Transact-SQL &#41;](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>См. также:  
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

