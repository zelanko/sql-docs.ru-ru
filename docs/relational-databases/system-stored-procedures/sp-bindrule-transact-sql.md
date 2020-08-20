---
description: sp_bindrule (Transact-SQL)
title: sp_bindrule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindrule_TSQL
- sp_bindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindrule
ms.assetid: 2606073e-c52f-498d-a923-5026b9d97e67
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c06a99b6c4e5f248df477e147f45b10c7f566f04
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493511"
---
# <a name="sp_bindrule-transact-sql"></a>sp_bindrule (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Привязывает правило к столбцу или к псевдониму типа данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Вместо этого используйте ограничения[UNIQUE и Check](../../relational-databases/tables/unique-constraints-and-check-constraints.md) . ПРОВЕРОЧные ограничения создаются с помощью ключевого слова CHECK в инструкциях [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) или [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_bindrule [ @rulename = ] 'rule' ,   
     [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rulename = ] 'rule'` Имя правила, созданного инструкцией CREATE RULE. *rule* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @objname = ] 'object_name'` Таблица и столбец или псевдоним типа данных, к которому должно быть привязано правило. Правило не может быть привязано к **text**, **ntext**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, определяемому пользователем типу CLR или столбцу **timestamp**. Правило не может быть привязано к вычисляемому столбцу.  
  
 *object_name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию. Если *object_name* является именем, сопоставленным с одним компонентом, оно разрешается как псевдоним типа данных. Если имя двух- или трехкомпонентное, оно рассматривается как таблица и столбец; в случае неудачи разрешения имя рассматривается как псевдоним типа данных. По умолчанию существующие столбцы типа данных псевдонима наследуют *правило* , если только правило не привязано непосредственно к столбцу.  
  
> [!NOTE]  
>  *object_name* могут содержать символы квадратных скобок **[** и **]** в качестве символов с разделителями. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
> [!NOTE]  
>  Правила, созданные на основе выражений, которые используют псевдоним типов данных, могут быть привязаны к столбцам или типам данных псевдонима, но не могут быть скомпилированы, если на них ссылаются. Избегайте использования правил, созданных на основе псевдонима типов данных.  
  
`[ @futureonly = ] 'futureonly_flag'` Используется только при привязке правила к псевдониму типа данных. *future_only_flag* имеет тип **varchar (15)** и значение по умолчанию NULL. Этот параметр при задании значения **futureonly** предотвращает наследование нового правила существующими столбцами псевдонима типа данных. Если *futureonly_flag* имеет значение null, новое правило привязывается к любому столбцу псевдонима типа данных, который в настоящее время не имеет правила или который использует существующее правило типа данных псевдонима.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 К столбцу можно привязать новое правило (хотя рекомендуется использовать ПРОВЕРОЧное ограничение) или псевдоним типа данных с **sp_bindrule** без отмены привязки существующего правила. Старое правило замещается. Если правило привязано к столбцу с существующим ограничением CHECK, вычисляются все ограничения. Нельзя привязать правило к типу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Правило создается принудительно при выполнении инструкции INSERT, а не путем привязки. Символьное правило можно привязать к столбцу **числовых** типов данных, хотя такая операция вставки недопустима.  
  
 Существующие столбцы типа данных alias наследуют новое правило, если только *futureonly_flag* не задан как **futureonly**. Новые столбцы, определяемые как столбцы с типом данных псевдонима, всегда наследуют новое правило. Однако если предложение ALTER COLUMN инструкции ALTER TABLE меняет тип данных столбца на тип данных псевдонима, привязанный к правилу, то правило, привязанное к типу данных, не наследуется столбцом. Правило необходимо специально привязать к столбцу с помощью **sp_bindrule**.  
  
 При привязке правила к столбцу в таблицу **sys. Columns** добавляются связанные сведения. При привязке правила к псевдониму типа данных связанная информация добавляется в таблицу **sys. types** .  
  
## <a name="permissions"></a>Разрешения  
 Чтобы привязать правило к столбцу таблицы, необходимо разрешение ALTER на таблицу. Чтобы привязать правило к псевдониму типа данных, необходимо разрешение CONTROL на псевдоним типа данных или разрешение ALTER на схему, к которой принадлежит тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-binding-a-rule-to-a-column"></a>A. Привязка правила к столбцу  
 Предполагая, что правило с именем `today` было создано в текущей базе данных при помощи инструкции CREATE RULE, на следующем примере показано, как привязывает правило к столбцу `HireDate` таблицы `Employee`. При добавлении строки в `Employee` данные для столбца `HireDate` проверяются на соответствие правилу `today`.  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-rule-to-an-alias-data-type"></a>Б. Привязка правила к псевдониму типа данных  
 Предполагая существование правила с именем `rule_ssn` и типа данных псевдонима с именем `ssn`, следующий пример привязывает `rule_ssn` к `ssn`. В инструкции CREATE TABLE столбцы типа `ssn` наследуют правило `rule_ssn`. Существующие столбцы типа `ssn` также наследуют `rule_ssn` правило, если только для *futureonly_flag*не указано значение **futureonly** или к `ssn` нему напрямую привязано правило. Правила, привязанные к столбцам, всегда имеют преимущество перед теми, которые привязаны к типам данных.  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'rule_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonly_flag"></a>В. Использование аргумента futureonly_flag  
 На следующем примере показано, как привязать правило `rule_ssn` к типу данных псевдонима `ssn`. Так как указан `futureonly`, никакие существующие столбцы типа `ssn` не затрагиваются.  
  
```  
USE master;  
GO  
EXEC sp_bindrule rule_ssn, 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>Г. Использование идентификаторов с разделителями  
 В следующем примере показано использование идентификаторов с разделителями в параметре *object_name* .  
  
```  
USE master;  
GO  
CREATE TABLE [t.2] (c1 int) ;  
-- Notice the period as part of the table name.  
EXEC sp_bindrule rule1, '[t.2].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [УДАЛИТЬ правило &#40;Transact-SQL&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
