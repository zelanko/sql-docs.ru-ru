---
title: "REVOKE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa08be63c0d792ed1e0422860b55a0c8f2abdc8b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-transact-sql"></a>REVOKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

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
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
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
  
 *разрешение*  
 Имя разрешения. Допустимые сопоставления разрешений защищаемых объектов описаны в разделах, перечисленных в [синтаксис защищаемыми](#securable) далее в этом разделе.  
  
 *столбец*  
 Указывает имя столбца таблицы, для которого производится отмена разрешений. Необходимо поставить скобки.  
  
 *класс*  
 Указывает класс защищаемого объекта, для которого производится отмена разрешения. Квалификатор области **::** является обязательным.  
  
 *защищаемый объект*  
 Указывает защищаемый объект, для которого проводится отмена разрешения.  
  
 ЧТОБЫ | ИЗ *участника*  
 Имя участника. Участники, у которых может быть отменено разрешение на доступ к защищаемому объекту, различны. Дополнительные сведения о допустимых сочетаниях см. в разделах, перечисленных в [синтаксис защищаемыми](#securable) далее в этом разделе.  
  
 CASCADE  
 Указывает, что разрешение также отменяется и у участников, получивших доступ через текущего участника. Аргумент CASCADE необходимо использовать совместно с аргументом GRANT OPTION FOR.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *участника*  
 Используйте предложение AS участника для указания, что удаленный доступ, в которой были предоставлены участником, отличных. Предположим, что пользователь Mary является principal_id 12, и пользователь Raul является основной 15. Мария и Raul предоставить пользователю с именем Стивен те же разрешения. В таблице sys.database_permissions указать разрешения, дважды, но они будут вычислять разные grantor_prinicpal_id значение. Мария может отменить разрешение с помощью `AS RAUL` предложений, чтобы удалить Raul на предоставление разрешения.
 
Использование этой инструкции не предусматривает возможность олицетворять другого пользователя.  
  
## <a name="remarks"></a>Замечания  
 Полный синтаксис инструкции REVOKE является сложным. Предыдущая диаграмма синтаксиса была упрощена, чтобы продемонстрировать ее структуру. Полный синтаксис процедуры отмены разрешений на конкретные защищаемые объекты описан в разделах, перечисленных в [синтаксис защищаемыми](#securable) далее в этом разделе.  
  
 Инструкция REVOKE может использоваться для удаления уже выданных прав доступа, а инструкция DENY может использоваться, чтобы предотвратить получение участником определенного разрешения посредством инструкции GRANT.  
  
 Предоставление разрешения удаляет DENY или REVOKE для этого разрешения на данный защищаемый объект. Если то же разрешение запрещено для более высокой области действия, которая содержит данный защищаемый объект, то DENY имеет более высокий приоритет. Однако отмена разрешения на более высоком уровне не имеет более высокого приоритета.  
  
> [!CAUTION]  
>  Запрет (DENY) уровня таблицы имеет меньший приоритет, чем разрешение (GRANT) уровня столбца. Такая несогласованность в иерархии разрешений сохранена в целях обратной совместимости. В будущем выпуске она будет удалена.  
  
 Системная хранимая процедура sp_helprotect сообщает о разрешениях на доступ к защищаемым объектам уровня базы данных  
  
 Если при отзыве разрешения участником, получившем его с помощью аргумента GRANT OPTION, не был задан аргумент CASCADE, выполнение инструкции REVOKE завершается сбоем.  
  
## <a name="permissions"></a>Permissions  
 Участники, обладающие разрешениями CONTROL для защищаемых объектов, могут предоставлять разрешения на доступ к ним. Владельцы объектов могут отменить разрешения на доступ к ним.  
  
 Участники, управляющие выдачей разрешений CONTROL SERVER, например члены предопределенной роли сервера sysadmin, имеют право отзывать любое разрешение на доступ к любому защищаемому объекту сервера. Участники, заведующие выдачей разрешений CONTROL, например члены предопределенной роли базы данных db_owner, имеют право отзывать любое разрешение на доступ к любому защищаемому объекту базы данных. Участники, заведующие выдачей разрешений CONTROL в схеме, имеют право отменять любое разрешение на доступ к любому объекту внутри схемы.  
  
##  <a name="securable"></a>Синтаксис  
 В следующей таблице перечислены защищаемые объекты и разделы, в которых описывается синтаксис инструкций по работе с ними.  
  
|Защищаемый объект|Раздел|  
|---------------|-----------|  
|Роль приложения|[ОТОЗВАТЬ разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Сборка|[ОТОЗВАТЬ разрешения для сборки &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-assembly-permissions-transact-sql.md)|  
|Асимметричный ключ|[ОТОЗВАТЬ разрешения на асимметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-asymmetric-key-permissions-transact-sql.md)|  
|Группа доступности|[Группа доступности REVOKE разрешения &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)|  
|Сертификат|[ОТОЗВАТЬ сертификат разрешения &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-certificate-permissions-transact-sql.md)|  
|Контракт|[ОТЗЫВ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|База данных|[ОТОЗВАТЬ разрешения базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-permissions-transact-sql.md)|  
|Конечная точка|[ОТОЗВАТЬ разрешения конечной точки &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)|  
|Учетные данные области базы данных|[В области базы данных REVOKE учетных данных (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)|  
|Полнотекстовый каталог|[ОТОЗВАТЬ разрешения Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Полнотекстовый список стоп-слов|[ОТОЗВАТЬ разрешения Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Функция|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Имя входа|[ОТОЗВАТЬ разрешения участника на уровне сервера &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)|  
|Тип сообщений|[ОТЗЫВ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Объект|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Очередь|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Привязка удаленной службы|[ОТЗЫВ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Роль|[ОТОЗВАТЬ разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Маршрут|[ОТЗЫВ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|схема|[REVOKE разрешения схемы &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-schema-permissions-transact-sql.md)|  
|Список свойств поиска|[ОТОЗВАТЬ разрешения Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)|  
|Server|[ОТОЗВАТЬ разрешения Server &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-permissions-transact-sql.md)|  
|Служба|[ОТЗЫВ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Хранимая процедура|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Симметричный ключ|[ОТОЗВАТЬ разрешения на симметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)|  
|Синоним|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Системные объекты|[ОТОЗВАТЬ разрешения на системный объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)|  
|Таблица|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Тип|[Разрешения типа REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)|  
|Пользователь|[ОТОЗВАТЬ разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Просмотр|[ОТЗЫВ разрешений на объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Коллекция схем XML|[ОТОЗВАТЬ разрешения на коллекцию схем XML &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>См. также:  
 [Иерархия разрешений (ядро СУБД)](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

