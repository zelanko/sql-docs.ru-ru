---
title: "CREATE DEFAULT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_DEFAULT_TSQL
- CREATE DEFAULT
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], default
- default objects
- CREATE DEFAULT statement
- objects [SQL Server], creating
- DEFAULT definition
ms.assetid: 08475db4-7d90-486a-814c-01a99d783d41
caps.latest.revision: 47
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71c0f964d245be92fb8d2be19e074fbd34dd616e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-default-transact-sql"></a>CREATE DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает объект «Значение по умолчанию». Если этот объект привязан к столбцу или псевдониму типа данных, он указывает значение, которое должно вставляться в столбец (или во все столбцы в случае псевдонима типа данных), если при вставке значение не задано явно.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте определения по умолчанию, создаваемые с помощью ключевого слова DEFAULT инструкций ALTER TABLE и CREATE TABLE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE DEFAULT [ schema_name . ] default_name   
AS constant_expression [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы, которой принадлежит значение по умолчанию.  
  
 *default_name*  
 Имя значения по умолчанию. По умолчанию имена должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Указывать имя владельца по умолчанию не обязательно.  
  
 *constant_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) , содержащее только постоянные значения (не может включать имена столбцов или других объектов базы данных). Можно использовать любые константы, встроенные функции или математические выражения, за исключением тех, которые содержат типы данных псевдонимов. Нельзя использовать пользовательские функции. Заключите константы символьного типа и даты в одинарные кавычки (**"**); денежных данных, целое число со знаком, а констант с плавающей запятой не требуют кавычек. Двоичные данные должны сопровождаться знаком 0x, а денежные данные — знаком доллара ($). Тип значения по умолчанию должен соответствовать типу данных столбца.  
  
## <a name="remarks"></a>Замечания  
 Имя по умолчанию может быть создано только в текущей базе данных. Внутри базы данных имена по умолчанию должны быть уникальны в схеме. Когда создается значение по умолчанию, используйте **sp_bindefault** Чтобы привязать его к столбцу или псевдониму типа данных.  
  
 Если значение по умолчанию не совместимо со столбцом, к которому оно привязывается, то при попытке его вставки в столбец [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует сообщение об ошибке. Например, н/д не может использоваться как значение по умолчанию для **числовое** столбца.  
  
 Если значение является слишком длинным для столбца, к которому оно привязывается, то происходит его усечение.  
  
 Инструкции CREATE DEFAULT не могут использоваться в одном пакете с другими инструкциями [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Значение по умолчанию должен быть удален перед созданием нового с тем же именем, и привязка по умолчанию, выполнив **sp_unbindefault** перед его удалением.  
  
 Каждому столбцу соответствуют значение по умолчанию и связанное с ним правило, причем значение по умолчанию должно соответствовать правилу. Значение по умолчанию, не удовлетворяющее правилу, не будет вставлено, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет выдавать ошибку при каждой попытке подобной вставки.  
  
 При привязке к столбцу значение по умолчанию вставляется при следующих условиях.  
  
-   Значение вставляется неявным образом.  
  
-   При выполнении функции INSERT для вставки значений по умолчанию используются ключевые слова DEFAULT VALUES или DEFAULT.  
  
 Если при создании столбца было указано NOT NULL и не были созданы значения по умолчанию, то при попытке записи в данный столбец будет выдаваться сообщение об ошибке. В следующей таблице представлена связь между фактом существования значения по умолчанию и определением столбца как NULL или NOT NULL. Записи таблицы отображают результаты.  
  
|Определение столбца|Нет записи, значение по умолчанию отсутствует|Нет записи, присвоено значение по умолчанию|Введено NULL, значение по умолчанию отсутствует|Введено NULL, значение по умолчанию|  
|-----------------------|--------------------------|-----------------------|----------------------------|-------------------------|  
|**NULL**|NULL|значение по умолчанию|NULL|NULL|  
|**NOT NULL**|Ошибка|значение по умолчанию|ошибка|ошибка|  
  
 Чтобы переименовать значение по умолчанию, используйте **sp_rename**. Для отчета, на значение по умолчанию, используется **sp_help**.  
  
## <a name="permissions"></a>Permissions  
 Чтобы вызвать команду CREATE DEFAULT, пользователь должен обладать разрешением CREATE DEFAULT в текущей базе данных и разрешением ALTER на схему, в которой создается значение по умолчанию.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-simple-character-default"></a>A. Создание простого символьного значения по умолчанию  
 В следующем примере создается символьное значение по умолчанию с именем `unknown`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
CREATE DEFAULT phonedflt AS 'unknown';  
```  
  
### <a name="b-binding-a-default"></a>Б. Привязка значения по умолчанию  
 При выполнении следующего примера производится привязка созданного в примере A значения по умолчанию. Значение по умолчанию используется в случае, когда в столбце `Phone` таблицы `Contact` нет записи. Обратите внимание, что пропуск записи отличается от явного указания значения NULL в инструкции INSERT.  
  
 Выполнение следующей инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] заканчивается сбоем, так как не существует значения по умолчанию `phonedflt`. Данный пример служит только для демонстрационных целей.  
  
```tsql  
USE AdventureWorks2012;  
GO  
sp_bindefault 'phonedflt', 'Person.PersonPhone.PhoneNumber';  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Удалить &#40; по умолчанию Transact-SQL &#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [УДАЛИТЬ правило &#40; Transact-SQL &#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [sp_bindefault &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [Хранимая процедура sp_unbindefault &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  

