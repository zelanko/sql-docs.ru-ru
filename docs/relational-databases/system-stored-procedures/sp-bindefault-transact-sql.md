---
title: sp_bindefault (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_bindefault
- sp_bindefault_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindefault
ms.assetid: 3da70c10-68d0-4c16-94a5-9e84c4a520f6
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3e23435d6c0a2db3809722856b9daa6b2d66505
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="spbindefault-transact-sql"></a>sp_bindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Привязывает значение по умолчанию к столбцу или псевдониму типа данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Рекомендуется создавать определения по умолчанию с помощью ключевого слова DEFAULT [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) инструкции вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_bindefault [ @defname = ] 'default' ,   
    [ @objname = ] 'object_name'   
    [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@defname=** ] **"***по умолчанию***"**  
 Имя умолчания, созданного инструкцией CREATE DEFAULT. *по умолчанию* — **nvarchar(776)**, не имеет значения по умолчанию.  
  
 [  **@objname=** ] **"***object_name***"**  
 Имя таблицы и столбца или псевдоним типа данных, к которым будет привязано значение по умолчанию. *object_name* — **nvarchar(776)** без значения по умолчанию. *object_name* не может быть определен с **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, либо в среде CLR определяемые пользователем типы.  
  
 Если *object_name* — это имя одной части, оно рассматривается как псевдоним типа данных. Если оно двух- или трехкомпонентное, предпринимается попытка рассмотреть его как таблицу и столбец; в случае неудачи имя рассматривается как псевдоним типа данных. По умолчанию существующие столбцы типа данных псевдонима наследуют *по умолчанию*, если значение по умолчанию привязан к столбцу напрямую. Значение по умолчанию не могут быть привязаны к **текст**, **ntext**, **изображения**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, **timestamp**, или CLR определяемого пользователем типа столбца, столбец со свойством IDENTITY, вычисляемый столбец или столбец, уже имеет ограничение по умолчанию.  
  
> [!NOTE]  
>  *object_name* может содержать квадратные скобки **[]** как идентификаторы с разделителями. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 [ **@futureonly=** ] **'***futureonly_flag***'**  
 Используется только в случае, если значение по умолчанию привязывается к псевдониму типа данных. *Аргумент futureonly_flag* — **varchar(15)** значение по умолчанию NULL. Если значение этого параметра **futureonly**, существующие столбцы этого типа данных не могут наследовать новое значение по умолчанию. Этот аргумент никогда не используется при привязке значения по умолчанию к столбцу. Если *аргумента futureonly_flag* имеет значение NULL, новое значение по умолчанию привязывается ко всем столбцам с псевдонимом типа данных, в настоящее время имеют по умолчанию или используют существующее значение по умолчанию псевдонима типа данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Можно использовать **sp_bindefault** Чтобы привязать новое значение по умолчанию к столбцу, хотя предпочтительнее с помощью ограничений по умолчанию или к псевдониму типа данных без отмены привязки существующего значения по умолчанию. Старое значение по умолчанию переопределяется. Нельзя привязать значение по умолчанию к системному типу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или определяемого пользователем типу данных среды CLR. Если значение по умолчанию несовместимо со столбцом, к которому оно привязано, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] возвращает сообщение об ошибке при вставке значения по умолчанию, а не при его привязке.  
  
 Существующие столбцы типа данных псевдонима наследуют новое значение по умолчанию, если значение по умолчанию привязано непосредственно к их или *аргумента futureonly_flag* указывается как **futureonly**. Новые столбцы с псевдонимом типа данных всегда наследуют значение по умолчанию.  
  
 При привязке к столбцу значение по умолчанию, соответствующие сведения добавляются в **sys.columns** представления каталога. При привязке значения по умолчанию к псевдониму типа данных, соответствующие сведения добавляются в **sys.types** представления каталога.  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть владельцем таблицы или быть членом **sysadmin** предопределенной роли сервера или **db_owner** и **db_ddladmin** предопределенных ролей базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-binding-a-default-to-a-column"></a>A. Привязка значения по умолчанию к столбцу  
 Значение по умолчанию с именем `today` было определено в текущей базе данных с помощью инструкции CREATE DEFAULT. В следующем примере это значение по умолчанию привязывается к столбцу `HireDate` в таблице `Employee`. Каждый раз, когда в таблицу `Employee` добавляется строка, а данные для столбца `HireDate` не заданы, этот столбец получает значение по умолчанию `today`.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-default-to-an-alias-data-type"></a>Б. Привязка значения по умолчанию к псевдониму типа данных  
 Значение по умолчанию с именем `def_ssn` и псевдоним типа данных с именем `ssn` уже существуют. В следующем примере значение по умолчанию `def_ssn` привязывается к псевдониму `ssn`. Когда создается таблица, значение по умолчанию наследуется всеми столбцами, которым присвоен псевдоним типа данных `ssn`. Существующие столбцы типа **ssn** также наследуют значение по умолчанию **def_ssn**, пока не **futureonly** указан для *аргумента futureonly_flag* значение или, если столбец имеет значение по умолчанию напрямую привязанное к нему. Значения по умолчанию, которые привязаны к столбцам, всегда имеют приоритет над значениями по умолчанию, привязанными к псевдониму типа данных.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>В. Использование аргумента futureonly_flag  
 В следующем примере значение по умолчанию `def_ssn` привязывается к псевдониму типа данных `ssn`. Поскольку **futureonly** указан, никакие существующие столбцы типа `ssn` затрагиваются.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>Г. Использование идентификаторов с разделителями  
 В следующем примере показано использование идентификаторов с разделителями `[t.1]`в *object_name*.  
  
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
  
## <a name="see-also"></a>См. также  
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md)   
 [DROP DEFAULT (Transact-SQL)](../../t-sql/statements/drop-default-transact-sql.md)   
 [Хранимая процедура sp_unbindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
