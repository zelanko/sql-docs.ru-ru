---
title: sp_bindefault (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindefault
- sp_bindefault_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindefault
ms.assetid: 3da70c10-68d0-4c16-94a5-9e84c4a520f6
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 918f545dd0ea0ca30524a307f1ae6d30c3fafb61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046053"
---
# <a name="sp_bindefault-transact-sql"></a>sp_bindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Привязывает значение по умолчанию к столбцу или псевдониму типа данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Рекомендуется создавать определения по умолчанию с помощью ключевого слова DEFAULT инструкции [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_bindefault [ @defname = ] 'default' ,   
    [ @objname = ] 'object_name'   
    [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @defname = ] 'default'`Имя по умолчанию, созданное по УМОЛЧАНИю. *значение по умолчанию* — **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @objname = ] 'object_name'`Имя таблицы, столбца или псевдонима типа данных, к которому должна быть привязана привязка по умолчанию. *object_name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию. *object_name* не могут быть определены с определяемыми пользователем типами **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**или CLR.  
  
 Если *object_name* является именем, сопоставленным с одним компонентом, оно разрешается как псевдоним типа данных. Если оно двух- или трехкомпонентное, предпринимается попытка рассмотреть его как таблицу и столбец; в случае неудачи имя рассматривается как псевдоним типа данных. По умолчанию существующие столбцы псевдонима типа данных наследуют *значение по умолчанию*, если только значение по умолчанию не привязывается непосредственно к столбцу. Значение по умолчанию не может быть привязано к столбцу **Text**, **ntext**, **Image**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **timestamp**или определяемому пользователем типу данных CLR, столбцу со свойством Identity, вычисляемому столбцу или столбцу, у которого уже есть ограничение по умолчанию.  
  
> [!NOTE]  
>  *object_name* могут содержать квадратные скобки **[]** в качестве идентификаторов с разделителями. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'`Используется только при привязке значения по умолчанию к псевдониму типа данных. *futureonly_flag* имеет тип **varchar (15)** и значение по умолчанию NULL. Если этот параметр имеет значение **futureonly**, существующие столбцы этого типа данных не могут наследовать новое значение по умолчанию. Этот аргумент никогда не используется при привязке значения по умолчанию к столбцу. Если *futureonly_flag* имеет значение null, новое значение по умолчанию привязывается к любому столбцу псевдонима типа данных, который в настоящее время не имеет значения по умолчанию, или на основе существующего значения по умолчанию псевдонима типа данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 **Sp_bindefault** можно использовать для привязки нового значения по умолчанию к столбцу, хотя рекомендуется использовать ограничение по умолчанию или псевдоним типа данных без отмены привязки к существующему по умолчанию. Старое значение по умолчанию переопределяется. Нельзя привязать значение по умолчанию к системному типу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или определяемого пользователем типу данных среды CLR. Если значение по умолчанию несовместимо со столбцом, к которому оно привязано, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] возвращает сообщение об ошибке при вставке значения по умолчанию, а не при его привязке.  
  
 Существующие столбцы типа данных псевдонима наследуют новое значение по умолчанию, если только к ним не привязано значение по умолчанию или *futureonly_flag* указан как **futureonly**. Новые столбцы с псевдонимом типа данных всегда наследуют значение по умолчанию.  
  
 При привязке значения по умолчанию к столбцу в представление каталога **sys. Columns** добавляются связанные сведения. При привязке значения по умолчанию к псевдониму типа данных связанная информация добавляется в представление каталога **sys. types** .  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен владеть таблицей или членом предопределенной роли сервера **sysadmin** либо предопределенной роли базы данных **db_owner** и **db_ddladmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-binding-a-default-to-a-column"></a>A. Привязка значения по умолчанию к столбцу  
 Значение по умолчанию с именем `today` было определено в текущей базе данных с помощью инструкции CREATE DEFAULT. В следующем примере это значение по умолчанию привязывается к столбцу `HireDate` в таблице `Employee`. Каждый раз, когда в таблицу `Employee` добавляется строка, а данные для столбца `HireDate` не заданы, этот столбец получает значение по умолчанию `today`.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-default-to-an-alias-data-type"></a>Б. Привязка значения по умолчанию к псевдониму типа данных  
 Значение по умолчанию с именем `def_ssn` и псевдоним типа данных с именем `ssn` уже существуют. В следующем примере значение по умолчанию `def_ssn` привязывается к псевдониму `ssn`. Когда создается таблица, значение по умолчанию наследуется всеми столбцами, которым присвоен псевдоним типа данных `ssn`. Существующие столбцы типа **ssn** также наследуют **def_ssn**по умолчанию, если только для *futureonly_flag* не задано значение **futureonly** , или если только к столбцу не привязывается по умолчанию напрямую. Значения по умолчанию, которые привязаны к столбцам, всегда имеют приоритет над значениями по умолчанию, привязанными к псевдониму типа данных.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonly_flag"></a>В. Использование аргумента futureonly_flag  
 В следующем примере значение по умолчанию `def_ssn` привязывается к псевдониму типа данных `ssn`. Так как указан **futureonly** , существующие столбцы типа `ssn` не затрагиваются.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>Г. Использование идентификаторов с разделителями  
 В следующем примере показано использование идентификаторов с разделителями `[t.1]`, в *object_name*.  
  
```  
USE master;  
GO  
CREATE TABLE [t.1] (c1 int);   
-- Notice the period as part of the table name.  
EXEC sp_bindefault 'default1', '[t.1].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name,   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Создание &#40;по УМОЛЧАНИю для&#41;Transact-SQL](../../t-sql/statements/create-default-transact-sql.md)   
 [DROP &#40;по УМОЛЧАНИю&#41;Transact-SQL](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_unbindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
