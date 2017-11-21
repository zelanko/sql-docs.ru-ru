---
title: "СОЗДАТЬ правило (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RULE_TSQL
- CREATE RULE
- CREATE_RULE_TSQL
- RULE
dev_langs:
- TSQL
helpviewer_keywords:
- list rules [SQL Server]
- unbinding rules
- pattern rules [SQL Server]
- range rules [SQL Server]
- alias data types [SQL Server], rules
- CREATE RULE statement
- reports [SQL Server], rules
- status information [SQL Server], rules
- rules [SQL Server], precedence
- binding rules [SQL Server]
- rules [SQL Server], creating
ms.assetid: b016a289-3a74-46b1-befc-a13183be51e4
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f1893007dd699ffb002884a153ac72fa90fcd103
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-rule-transact-sql"></a>CREATE RULE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает объект, называемый правилом. Будучи привязанным к столбцу, имеющему псевдоним типа данных, правило определяет значения, которые могут быть вставлены в этот столбец.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этой инструкции рекомендуется применять проверку ограничений. Эти ограничения создаются при помощи ключевого слова CHECK инструкции CREATE TABLE или ALTER TABLE. Дополнительные сведения см. в статье [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).  
  
 К столбцу, имеющему псевдоним типа данных, можно привязать только одно правило. Однако кроме правила, со столбцом может быть связано одно или несколько ограничений CHECK. Если это так, соблюдаются все ограничивающие условия.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE RULE [ schema_name . ] rule_name   
AS condition_expression  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы, к которой относится правило.  
  
 *rule_name*  
 Имя нового правила. Имена правил должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Указывать имя владельца правила необязательно.  
  
 *condition_expression*  
 Условие или условия, определяющие правило. Правило может быть любым выражением, допустимым в предложении WHERE, и может включать такие элементы, как арифметические операторы, операторы отношений и предикаты (например IN, LIKE и BETWEEN). Правило не может ссылаться на столбцы или другие объекты базы данных. В правило могут входить встроенные функции, не ссылающиеся на объекты базы данных. Определяемые пользователем функции использовать в правилах нельзя.  
  
 *condition_expression* включает одну переменную. Знак (**@**) каждой локальной переменной предшествует. Выражение соответствует значению, введенному при помощи инструкции UPDATE или INSERT. Для представления значения при создании правила можно использовать любое имя или символ, но первым знаком должен быть знак (**@**).  
  
> [!NOTE]  
>  Не следует создавать правила с выражениями, в которых используются псевдонимы типа данных. Хотя создание таких правил и возможно, но после привязки правил к столбцам или псевдониму типа данных эти выражения компилироваться не будут.  
  
## <a name="remarks"></a>Замечания  
 Инструкцию CREATE RULE нельзя объединять с другими инструкциями [!INCLUDE[tsql](../../includes/tsql-md.md)] в одном пакете. Правила не распространяются на данные, существовавшие в базе данных на момент создания правил, и не могут быть привязаны к системным типам данных.  
  
 Правило может быть создано только в текущей базе данных. После создания правила, выполните **sp_bindrule** для привязки правила к столбцу или псевдониму типа данных. Правило должно быть совместимо с типом столбца. Например «@value LIKE A %» не может использоваться в качестве правила для числового столбца. Правило не может быть привязано к **текст**, **ntext**, **изображения**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, определяемого пользователем типа CLR или **timestamp**столбца. Правило не может быть привязано к вычисляемому столбцу.  
  
 Символьные константы и константы-даты следует заключать в одиночные кавычки ('), а двоичные константы — предварять знаками 0x. Если правило несовместимо со столбцом, к которому оно привязано, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] возвращает сообщение об ошибке при попытке вставки значения в столбец, но не во время привязки правила.  
  
 Правило, привязанное к псевдониму типа данных, активируется только при попытке вставить значение в столбец типа данных псевдонима или обновить такой столбец. Переменные в правилах не проверяются, поэтому не следует присваивать переменным псевдонима типа данных значения, которые были бы отклонены правилом, привязанным к столбцу такого же типа.  
  
 Для получения отчета о правиле, используйте **sp_help**. Для отображения текста правила выполните **sp_helptext** с именем правила в качестве параметра. Для переименования правила следует использовать **sp_rename**.  
  
 Правило должно удаляться при помощи DROP RULE, прежде чем создается новый файл с тем же именем, и правило должно быть существующего **sp_unbindrule** перед его удалением. Чтобы отменить привязку правила к столбцу, используйте **sp_unbindrule**.  
  
 Можно привязать к столбцу или типу данных новое правило без отмены привязки предыдущего правила; в этом случае старое правило будет переопределено новым. Правила, привязанные к столбцам, всегда имеют больший приоритет, чем правила, привязанные к псевдонимам типа данных. Привязка правила к столбцу приводит к замене правила, уже привязанного к псевдониму типа данных, соответствующему данному столбцу. Однако привязка правила к типу данных не заменяет правило, привязанное к столбцу, имеющему этот псевдоним типа данных. Следствия привязки правил к столбцам и псевдонимам типа данных, к которым уже привязаны правила, поясняет следующая таблица:  
  
|Сущность, к которой привязывается новое правило|Старое правило привязано к<br /><br /> псевдоним типа данных|Старое правило привязано к<br /><br /> Столбец|  
|-----------------------|-------------------------------------------|----------------------------------|  
|Псевдоним типа данных|Старое правило заменяется.|Изменений нет|  
|Столбец|Старое правило заменяется.|Старое правило заменяется.|  
  
 Если столбец имеет и значение по умолчанию и привязанное к нему правило, значение по умолчанию должно попадать в диапазон, определяемый правилом. Значение по умолчанию, конфликтующее с правилом, никогда не вставляется в столбец. При попытке вставить в столбец такое значение по умолчанию ядро СУБД SQL Server формирует сообщение об ошибке.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции CREATE RULE необходимо как минимум разрешение CREATE RULE, связанное с текущей базой данных, и разрешение ALTER, связанное со схемой, в которой создается правило.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-rule-with-a-range"></a>A. Создание правила с диапазоном  
 Следующий код создает правило, ограничивающее диапазон целых чисел, которые могут быть вставлены в столбец или столбцы, связанные с данным правилом.  
  
```  
CREATE RULE range_rule  
AS   
@range>= $1000 AND @range <$20000;  
```  
  
### <a name="b-creating-a-rule-with-a-list"></a>Б. Создание правила со списком  
 Следующий код создает правило, ограничивающее значения, вставляемые в столбец или столбцы (к которым привязано данное правило) только теми значениями, которые указаны в правиле.  
  
```  
CREATE RULE list_rule  
AS   
@list IN ('1389', '0736', '0877');  
```  
  
### <a name="c-creating-a-rule-with-a-pattern"></a>В. Создание правила с шаблоном  
 Следующий код создает правило, позволяющее вставлять в столбец только значения, начинающиеся на два любых символа, за которыми следуют дефис (`-`), любое число символов или не следует никаких символов, и завершающиеся целым числом из диапазона `0`—`9`.  
  
```  
CREATE RULE pattern_rule   
AS  
@value LIKE '__-%[0-9]'  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Удалить &#40; по умолчанию Transact-SQL &#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [УДАЛИТЬ правило &#40; Transact-SQL &#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [sp_bindrule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindrule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

