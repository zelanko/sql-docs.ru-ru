---
title: sp_helprotect (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprotect
- sp_helprotect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprotect
ms.assetid: faaa3e40-1c95-43c2-9fdc-c61a1d3cc0c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3806476ffec61c155121f3238fefa8e08f689ad2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772135"
---
# <a name="sp_helprotect-transact-sql"></a>sp_helprotect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает отчет со сведениями о разрешениях пользователя на объект или инструкцию в текущей базе данных.  
  
> [!IMPORTANT]  
>  **sp_helprotect** не возвращает сведения о защищаемых объектах, которые появились в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Вместо этого используйте представление [sys. database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) и [fn_builtin_permissions](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md) .  
  
 Не включает разрешения, которые всегда присваиваются предопределенным ролям сервера или базы данных. Не включает имена входа и пользователей, которые получают разрешения на основе своего членства в роли.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helprotect [ [ @name = ] 'object_statement' ]   
     [ , [ @username = ] 'security_account' ]   
     [ , [ @grantorname = ] 'grantor' ]   
     [ , [ @permissionarea = ] 'type' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'object_statement'`Имя объекта в текущей базе данных или инструкция, которая имеет разрешения для отчета. *object_statement* имеет тип **nvarchar (776)** и значение по умолчанию NULL, которое возвращает все разрешения объекта и инструкции. Если значение представляет объект (таблицы, представление, хранимая процедура или расширенная хранимая процедура), в текущей базе данных этот объект должен быть допустимым. Имя объекта может включать квалификатор владельца в форму _owner_**.** _объект_.  
  
 Если *object_statement* является инструкцией, это может быть инструкция CREATE.  
  
`[ @username = ] 'security_account'`Имя участника, для которого возвращаются разрешения. Аргумент *security_account* имеет тип **sysname**и значение по умолчанию NULL, которое возвращает все субъекты в текущей базе данных. *security_account* должен существовать в текущей базе данных.  
  
`[ @grantorname = ] 'grantor'`Имя участника, которому предоставлены разрешения. *Grant* имеет тип **sysname**и значение по умолчанию NULL, которое возвращает всю информацию о разрешениях, предоставленных любым участником в базе данных.  
  
`[ @permissionarea = ] 'type'`Символьная строка, указывающая, следует ли отображать разрешения объекта (символьная строка **o**), разрешения инструкции (символьные **строки) или**оба (**ОС**). *Type имеет тип* **varchar (10)** и значение по умолчанию **OS**. *тип* может быть любым сочетанием **o** и **s**, с запятыми или пробелами между **o** и **s**или без них.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Владелец**|**sysname**|Имя владельца объекта.|  
|**Объект**|**sysname**|Имя объекта.|  
|**Участник**|**sysname**|Имя участника, которому были предоставлены разрешения.|  
|**GRANTOR**|**sysname**|Имя участника, предоставившего разрешения.|  
|**протекттипе**|**nvarchar (10)**|Имя типа защиты:<br /><br /> GRANT REVOKE|  
|**Действие**|**nvarchar(60)**|Имя разрешения. Инструкции с допустимыми разрешениями зависят от типа объекта.|  
|**Столбец**|**sysname**|Тип разрешения:<br /><br /> All = разрешение затрагивает все текущие столбцы объекта.<br /><br /> New = разрешение затрагивает все новые столбцы, которые могут быть изменены для объекта в будущем (с помощью инструкции ALTER).<br /><br /> All+New = сочетание All и New.<br /><br /> Возвращает точку, если тип разрешения не применяется к столбцам.|  
  
## <a name="remarks"></a>Примечания  
 Все аргументы в следующей процедуре являются необязательными. При выполнении без аргументов процедура `sp_helprotect` отображает все разрешения, которые были предоставлены или запрещены в текущей базе данных.  
  
 При указании некоторых, но не всех аргументов используйте именованные аргументы либо указывайте `NULL` в качестве заполнителя опущенных аргументов. Например, для получения отчета обо всех разрешениях, которые может предоставить участник, владеющий базой данных (`dbo`), выполните следующее:  
  
```  
EXEC sp_helprotect NULL, NULL, dbo;  
```  
  
 либо  
  
```  
EXEC sp_helprotect @grantorname = 'dbo';  
```  
  
 Данные в отчете сортируются по категории разрешения, владельцу, объекту, получателю разрешения, участнику, предоставившему разрешение, категории типа защиты, типу защиты, действию и столбцу идентификатора.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
 Полученные данные подлежат ограничениям на доступ к метаданным. Сущности, на которые участник не имеет разрешения, не показаны. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-the-permissions-for-a-table"></a>A. Список разрешений для таблицы  
 В следующем примере выводится список разрешений для таблицы `titles`.  
  
```  
EXEC sp_helprotect 'titles';  
```  
  
### <a name="b-listing-the-permissions-for-a-user"></a>Б. Список разрешений для пользователя  
 В следующем примере выводится список всех разрешений, которые пользователь `Judy` имеет в текущей базе данных.  
  
```  
EXEC sp_helprotect NULL, 'Judy';  
```  
  
### <a name="c-listing-the-permissions-granted-by-a-specific-user"></a>В. Список разрешений, предоставленных указанным пользователем  
 В следующем примере выводится список всех разрешений, которые были предоставлены пользователем `Judy` в текущей базе данных, с использованием `NULL` в качестве заполнителей пропущенных параметров.  
  
```  
EXEC sp_helprotect NULL, NULL, 'Judy';  
```  
  
### <a name="d-listing-the-statement-permissions-only"></a>Г. Список разрешений только на инструкции  
 В следующем примере выводится список всех разрешений на инструкции в текущей базе данных с использованием `NULL` в качестве заполнителей пропущенных параметров.  
  
```  
EXEC sp_helprotect NULL, NULL, NULL, 's';   
```  
  
### <a name="e-listing-the-permissions-for-a-create-statement"></a>Д. Список разрешений для инструкции CREATE  
 В следующем примере приведен список всех пользователей, которым предоставлено разрешение CREATE TABLE.  
  
```  
EXEC sp_helprotect @name = 'CREATE TABLE';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DENY &#40;&#41;Transact-SQL](../../t-sql/statements/deny-transact-sql.md)   
 [ПРЕДОСТАВЛЕНИЕ &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [ОТОЗВАТЬ &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
