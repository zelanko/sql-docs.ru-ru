---
title: REVOKE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- REVOKE_TSQL
- REVOKE
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- REVOKE statement, Transact-SQL syntax
- removing permissions
- server-level securables [SQL Server]
- deleting permissions
- revoking permissions [SQL Server]
- REVOKE statement
- denying permissions [SQL Server], removing
- database-level securables [SQL Server]
- granting permissions [SQL Server], removing
- permissions [SQL Server], revoking
- dropping permissions
ms.assetid: 9d31d3e7-0883-45cd-bf0e-f0361bbb0956
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: af52c3516d374d02e19abb757765cc23adad4fe3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="revoke-transact-sql"></a>REVOKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет разрешение, выданное или запрещенное ранее.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for REVOKE  
REVOKE [ GRANT OPTION FOR ]  
      {   
        [ ALL [ PRIVILEGES ] ]  
        |  
                permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      }  
      [ ON [ class :: ] securable ]   
      { TO | FROM } principal [ ,...n ]   
      [ CASCADE] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
REVOKE   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    [ FROM | TO ] principal [ ,...n ]  
    [ CASCADE ]  
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
 GRANT OPTION FOR  
 Указывает, что возможность предоставлять указанное разрешение будет отменена. Данный аргумент необходим при использовании аргумента CASCADE.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 ALL  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Этот параметр не отменяет все возможные разрешения. Указание аргумента ALL при отзыве отменяет следующие разрешения.  
  
-   Если защищаемым объектом является база данных, аргумент ALL относится к разрешениям BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE и CREATE VIEW.  
  
-   Если защищаемым объектом является скалярная функция, аргумент ALL относится к разрешениям EXECUTE и REFERENCES.  
  
-   Если защищаемым объектом является функция с табличным значением, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
-   Если защищаемая сущность является хранимой процедурой, аргумент ALL подразумевает разрешение EXECUTE.  
  
-   Если защищаемым объектом является таблица, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
-   Если защищаемым объектом является представление, аргумент ALL относится к разрешениям DELETE, INSERT, REFERENCES, SELECT и UPDATE.  
  
> [!NOTE]  
>  Синтаксис REVOKE ALL является устаревшим. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого отменяйте конкретные разрешения.  
  
 PRIVILEGES  
 Включено для обеспечения совместимости с требованиями ISO. Не изменяет работу ALL.  
  
 *permission*  
 Имя разрешения. Допустимые сопоставления разрешений с защищаемыми объектами описаны в разделах, перечисленных ниже в подразделе [Синтаксис инструкций при работе с различными защищаемыми объектами](#securable) данного раздела.  
  
 *column*  
 Указывает имя столбца таблицы, для которого производится отмена разрешений. Необходимо поставить скобки.  
  
 *class*  
 Указывает класс защищаемого объекта, для которого производится отмена разрешения. Квалификатор области **::** является обязательным.  
  
 *securable*  
 Указывает защищаемый объект, для которого проводится отмена разрешения.  
  
 TO | FROM *principal*  
 Имя участника. Участники, у которых может быть отменено разрешение на доступ к защищаемому объекту, различны. Дополнительные сведения о допустимых сочетаниях см. в разделе [Синтаксис инструкций при работе с различными защищаемыми объектами](#securable), приведенном ниже.  
  
 CASCADE  
 Указывает, что разрешение также отменяется и у участников, получивших доступ через текущего участника. Аргумент CASCADE необходимо использовать совместно с аргументом GRANT OPTION FOR.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *principal*  
 Используйте предложение AS участника для указания того, что вы отменяете разрешение, которое было предоставлено участником, отличным от вас. Предположим, что пользователь Мария — это участник 12, пользователь Павел — участник 15. Мария и Павел предоставляют пользователю Степану то же разрешение. В таблице sys.database_permissions разрешения будут указаны дважды, но у каждого из них будет разное значение grantor_prinicpal_id. Мария может отменить разрешение с помощью предложения `AS RAUL`, чтобы удалить право Павла на предоставление разрешения.
 
AS в данной инструкции не дает возможность олицетворять другого пользователя.  
  
## <a name="remarks"></a>Примечания  
 Полный синтаксис инструкции REVOKE является сложным. Предыдущая диаграмма синтаксиса была упрощена, чтобы продемонстрировать ее структуру. Полный синтаксис процедуры отмены разрешений для различных защищаемых объектов описывается в разделах, перечисленных ниже в подразделе [Синтаксис инструкций при работе с различными защищаемыми объектами](#securable) данного раздела.  
  
 Инструкция REVOKE может использоваться для удаления уже выданных прав доступа, а инструкция DENY может использоваться, чтобы предотвратить получение участником определенного разрешения посредством инструкции GRANT.  
  
 Предоставление разрешения удаляет DENY или REVOKE для этого разрешения на данный защищаемый объект. Если то же разрешение запрещено для более высокой области действия, которая содержит данный защищаемый объект, то DENY имеет более высокий приоритет. Однако отмена разрешения на более высоком уровне не имеет более высокого приоритета.  
  
> [!CAUTION]  
>  Запрет (DENY) уровня таблицы имеет меньший приоритет, чем разрешение (GRANT) уровня столбца. Такая несогласованность в иерархии разрешений сохранена в целях обратной совместимости. В будущем выпуске она будет удалена.  
  
 Системная хранимая процедура sp_helprotect сообщает о разрешениях на доступ к защищаемым объектам уровня базы данных  
  
 Если при отзыве разрешения участником, получившем его с помощью аргумента GRANT OPTION, не был задан аргумент CASCADE, выполнение инструкции REVOKE завершается сбоем.  
  
## <a name="permissions"></a>Разрешения  
 Участники, обладающие разрешениями CONTROL для защищаемых объектов, могут предоставлять разрешения на доступ к ним. Владельцы объектов могут отменить разрешения на доступ к ним.  
  
 Участники, управляющие выдачей разрешений CONTROL SERVER, например члены предопределенной роли сервера sysadmin, имеют право отзывать любое разрешение на доступ к любому защищаемому объекту сервера. Участники, заведующие выдачей разрешений CONTROL, например члены предопределенной роли базы данных db_owner, имеют право отзывать любое разрешение на доступ к любому защищаемому объекту базы данных. Участники, заведующие выдачей разрешений CONTROL в схеме, имеют право отменять любое разрешение на доступ к любому объекту внутри схемы.  
  
##  <a name="securable"></a> Синтаксис инструкций при работе с различными защищаемыми объектами  
 В следующей таблице перечислены защищаемые объекты и разделы, в которых описывается синтаксис инструкций по работе с ними.  
  
|Защищаемый объект|Раздел|  
|---------------|-----------|  
|Роль приложения|[REVOKE, отмена разрешений на субъекта базы данных (Transact-SQL)](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Сборка|[REVOKE, отмена разрешений на сборку (Transact-SQL)](../../t-sql/statements/revoke-assembly-permissions-transact-sql.md)|  
|Асимметричный ключ|[REVOKE, отмена разрешений на асимметричный ключ (Transact-SQL)](../../t-sql/statements/revoke-asymmetric-key-permissions-transact-sql.md)|  
|Группа доступности|[REVOKE, отмена разрешений на группу доступности (Transact-SQL)](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)|  
|Сертификат|[REVOKE, отмена разрешений на сертификат (Transact-SQL)](../../t-sql/statements/revoke-certificate-permissions-transact-sql.md)|  
|Контракт|[REVOKE, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|База данных|[REVOKE, отмена разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-database-permissions-transact-sql.md)|  
|Конечная точка|[REVOKE, отмена разрешений на конечную точку (Transact-SQL)](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)|  
|Учетные данные для базы данных|[REVOKE, отмена учетных данных для базы данных (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)|  
|Полнотекстовый каталог|[REVOKE, отмена разрешений на полнотекстовые объекты (Transact-SQL)](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Полнотекстовый список стоп-слов|[REVOKE, отмена разрешений на полнотекстовые объекты (Transact-SQL)](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Компонент|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Имя входа|[REVOKE, отмена разрешений участника на уровне сервера (Transact-SQL)](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)|  
|Тип сообщений|[REVOKE, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Объект|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Очередь|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Привязка удаленной службы|[REVOKE, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Роль|[REVOKE, отмена разрешений на субъекта базы данных (Transact-SQL)](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Маршрут|[REVOKE, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Схема|[REVOKE, отмена разрешений на схему (Transact-SQL)](../../t-sql/statements/revoke-schema-permissions-transact-sql.md)|  
|Список свойств поиска|[REVOKE, отмена разрешений на список свойств поиска (Transact-SQL)](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)|  
|Сервер|[REVOKE, отмена разрешений на сервер (Transact-SQL)](../../t-sql/statements/revoke-server-permissions-transact-sql.md)|  
|Служба|[REVOKE, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Хранимая процедура|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Симметричный ключ|[REVOKE, отмена разрешений на симметричный ключ (Transact-SQL)](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)|  
|Синоним|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Системные объекты|[REVOKE, отмена разрешений на системный объект (Transact-SQL)](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)|  
|Таблица|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Тип|[REVOKE, отмена разрешений на тип (Transact-SQL)](../../t-sql/statements/revoke-type-permissions-transact-sql.md)|  
|Пользователь|[REVOKE, отмена разрешений на субъекта базы данных (Transact-SQL)](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Представление|[REVOKE, отмена разрешений на объект (Transact-SQL)](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Коллекция схем XML|[REVOKE, отмена разрешений на коллекцию XML-схем (Transact-SQL)](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>См. также  
 [Иерархия разрешений (ядро СУБД)](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  
