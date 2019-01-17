---
title: MERGE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MERGE
- MERGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating data [SQL Server]
- modifying data [SQL Server], MERGE statement
- MERGE statement [SQL Server]
- adding data
- DML [SQL Server], MERGE statement
- table modifications [SQL Server], MERGE statement
- data manipulation language [SQL Server], MERGE statement
- inserting data
ms.assetid: c17996d6-56a6-482f-80d8-086a3423eecc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 939ba409a75d332d0aba97aa972db2ba9eecaf7a
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53980020"
---
# <a name="merge-transact-sql"></a>MERGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

> [!div class="nextstepaction"]
> [Помогите улучшить документацию по SQL Server!](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

Выполняет операции вставки, обновления или удаления для целевой таблицы на основе результатов соединения с исходной таблицей. Например, можно синхронизировать две таблицы путем вставки, обновления или удаления строк в одной таблице на основании отличий, найденных в другой таблице.  
  
 **Совет для повышения производительности**. Условное поведение, описанное для оператора MERGE лучше использовать, если две таблицы содержат сложное сочетание сопоставленных характеристик. Например, вставка строки, если она не существует, или обновление строки, если она не совпадает. При обновлении только одной таблицы на основе строк из другой таблицы, повышения производительности и масштабируемости можно добиться с помощью базовых операторов INSERT, UPDATE и DELETE. Пример:  
  
```  
INSERT tbl_A (col, col2)  
SELECT col, col2   
FROM tbl_B   
WHERE NOT EXISTS (SELECT col FROM tbl_A A2 WHERE A2.col = tbl_B.col);  
```  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[ WITH <common_table_expression> [,...n] ]  
MERGE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ INTO ] <target_table> [ WITH ( <merge_hint> ) ] [ [ AS ] table_alias ]  
    USING <table_source>   
    ON <merge_search_condition>  
    [ WHEN MATCHED [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ WHEN NOT MATCHED [ BY TARGET ] [ AND <clause_search_condition> ]  
        THEN <merge_not_matched> ]  
    [ WHEN NOT MATCHED BY SOURCE [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ <output_clause> ]  
    [ OPTION ( <query_hint> [ ,...n ] ) ]      
;  
  
<target_table> ::=  
{   
    [ database_name . schema_name . | schema_name . ]  
  target_table  
}  
  
<merge_hint>::=  
{  
    { [ <table_hint_limited> [ ,...n ] ]  
    [ [ , ] INDEX ( index_val [ ,...n ] ) ] }  
}  
  
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ] [ <tablesample_clause> ]   
        [ WITH ( table_hint [ [ , ]...n ] ) ]   
  | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
  | user_defined_function [ [ AS ] table_alias ]  
  | OPENXML <openxml_clause>   
  | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]   
  | <joined_table>   
  | <pivoted_table>   
  | <unpivoted_table>   
}  
  
<merge_search_condition> ::=  
    <search_condition>  
  
<merge_matched>::=  
    { UPDATE SET <set_clause> | DELETE }  
  
<set_clause>::=  
SET  
  { column_name = { expression | DEFAULT | NULL }  
  | { udt_column_name.{ { property_name = expression  
                        | field_name = expression }  
                        | method_name ( argument [ ,...n ] ) }  
    }  
  | column_name { .WRITE ( expression , @Offset , @Length ) }  
  | @variable = expression  
  | @variable = column = expression  
  | column_name { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable = column { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  } [ ,...n ]   
  
<merge_not_matched>::=  
{  
    INSERT [ ( column_list ) ]   
        { VALUES ( values_list )  
        | DEFAULT VALUES }  
}  
  
<clause_search_condition> ::=  
    <search_condition>  
  
<search condition> ::=  
    MATCH(<graph_search_pattern>) | <search_condition_without_match> | <search_condition> AND <search_condition>
    
<search_condition_without_match> ::=
    { [ NOT ] <predicate> | ( <search_condition_without_match> ) 
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition_without_match> ) } ]   
[ ,...n ]  

<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '< contains_search_condition >' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery ) }   

<graph_search_pattern> ::=
    { <node_alias> { 
                      { <-( <edge_alias> )- } 
                    | { -( <edge_alias> )-> }
                    <node_alias> 
                   } 
    }
  
<node_alias> ::=
    node_table_name | node_table_alias 

<edge_alias> ::=
    edge_table_name | edge_table_alias

<output_clause>::=  
{  
    [ OUTPUT <dml_select_list> INTO { @table_variable | output_table }  
        [ (column_list) ] ]  
    [ OUTPUT <dml_select_list> ]  
}  
  
<dml_select_list>::=  
    { <column_name> | scalar_expression }   
        [ [AS] column_alias_identifier ] [ ,...n ]  
  
<column_name> ::=  
    { DELETED | INSERTED | from_table_name } . { * | column_name }  
    | $action  
```  
  
## <a name="arguments"></a>Аргументы  
 WITH \<common_table_expression>  
 Указывает определенный в области инструкции MERGE временный именованный результирующий набор или представление, которые называются обобщенным табличным выражением. Результирующий набор, на который ссылается инструкция MERGE, является производным простого запроса. Дополнительные сведения см. в разделе [WITH common_table_expression (Transact-SQL)](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 TOP ( *expression* ) [ PERCENT ]  
 Указывает количество или процент строк, которые подпадают под эту операцию. *expression* может быть либо числом, либо процентом от числа строк. Строки, на которые ссылается выражение TOP, не расположены в определенном порядке. Дополнительные сведения см. в разделе [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md).  
  
 Предложение TOP применяется после соединения всей исходной таблицы и всей целевой таблицы и удаления соединенных строк, которые не рассматриваются как предназначенные для выполнения операций вставки, обновления или удаления. Предложение TOP дополнительно сокращает количество соединенных строк до указанного значения, а затем к оставшимся соединенным строкам применяются операции вставки, обновления или удаления без учета порядка. Иными словами, порядок, в котором строки подвергаются операциям, определенным в предложениях WHEN, не задан. Например, указание значения TOP (10) затрагивает 10 строк. Из них 7 могут быть обновлены и 3 вставлены или 1 может быть удалена, 5 обновлено и 4 вставлено и т. д.  
  
 Инструкция MERGE выполняет полный просмотр исходной и целевой таблиц, поэтому при использовании предложения TOP для изменения большой таблицы путем создания нескольких пакетов производительность ввода-вывода может снизиться. В этом случае необходимо обеспечить, чтобы во всех подряд идущих пакетах осуществлялась обработка новых строк.  
  
 *database_name*  
 Имя базы данных, в которой расположена таблица *target_table*.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица *target_table*.  
  
 *target_table*  
 Таблица или представление, с которыми выполняется сопоставление строк данных из таблицы \<table_source> по условию \<clause_search_condition>. Таблица *target_table* является целевым объектом любых операций вставки, обновления или удаления, указанных предложениями WHEN в инструкции MERGE.  
  
 Если аргумент таблица *target_table* является представлением, то все действия, выполняемые с ней, должны удовлетворять условиям для обновления представлений. Дополнительные сведения см. в разделе [Изменение данных через представление](../../relational-databases/views/modify-data-through-a-view.md).  
  
 *target_table* не может быть удаленной таблицей. Определить какие-либо правила для таблицы *target_table* нельзя.  
  
 [ AS ] *table_alias*  
 Альтернативное имя, используемое для указания ссылок на эту таблицу.  
  
 USING \<table_source>  
 Указывается источник данных, который сопоставляется со строками данных в таблице *target_table* на основе условия \<merge_search condition>. Результат этого совпадения обуславливает действия, которые выполняются предложениями WHEN инструкции MERGE. Аргумент \<table_source> может быть удаленной таблицей или производной таблицей, которая обращается к удаленным таблицам. 
  
 Аргументом \<table_source> может быть производная таблица, использующая [!INCLUDE[tsql](../../includes/tsql-md.md)] [конструктор табличных значений](../../t-sql/queries/table-value-constructor-transact-sql.md) для построения таблицы путем указания нескольких строк.  
  
 Дополнительные сведения о синтаксисе и аргументах этого предложения см. в разделе [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  
  
 ON \<merge_search_condition>  
 Указываются условия, при которых \<table_source> соединяется с таблицей *target_table* для сопоставления. 
  
> [!CAUTION]  
>  Важно указать только те столбцы из целевой таблицы, которые используются для поиска совпадений. Иными словами, необходимо указать столбцы целевой таблицы, которые сравниваются с соответствующим столбцом исходной таблицы. Не рекомендуется повышать производительность запроса за счет фильтрации строк в целевой таблице в предложении ON, как при указании `AND NOT target_table.column_x = value`. Это может привести к получению непредвиденных и неверных результатов.  
  
 WHEN MATCHED THEN \<merge_matched>  
 Указывается, что все строки *target_table*, которые соответствуют строкам, возвращенным \<table_source> ON \<merge_search_condition>, и удовлетворяют дополнительным условиям поиска, обновляются или удаляются в соответствии с предложением \<merge_matched>.  
  
 Инструкция MERGE может иметь не больше двух предложений WHEN MATCHED. Если указаны два предложения, первое предложение должно сопровождаться предложением AND \<search_condition>. Для любой строки второе предложение WHEN MATCHED применяется только в тех случаях, если не применяется первое. Если имеются два предложения WHEN MATCHED, одно должно указывать действие UPDATE, а другое — действие DELETE. Если действие UPDATE указано в предложении \<merge_matched> и более одной строки в \<table_source> соответствует строке в *target_table* на основе \<merge_search_condition>, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку. Инструкцию MERGE нельзя использовать для обновления одной строки более одного раза, а также использовать для обновления и удаления одной и той же строки.  
  
 WHEN NOT MATCHED [ BY TARGET ] THEN \<merge_not_matched>  
 Указывает, что строка вставлена в таблицу *target_table* для каждой строки, возвращенной выражением \<table_source> ON \<merge_search_condition>, которая не соответствует строке в таблице *target_table*, но удовлетворяет дополнительному условию поиска (при наличии такового). Значения для вставки указываются с помощью предложения \<merge_not_matched>. Инструкция MERGE может иметь только одно предложение WHEN MATCHED.  
  
 WHEN NOT MATCHED BY SOURCE THEN \<merge_matched>  
 Указывается, что все строки *target_table*, которые не соответствуют строкам, возвращенным \<table_source> ON \<merge_search_condition> и удовлетворяют дополнительным условиям поиска, обновляются или удаляются в соответствии с предложением \<merge_matched>.  
  
 Инструкция MERGE может иметь не более двух предложений WHEN NOT MATCHED BY SOURCE. Если указаны два предложения, то первое предложение должно сопровождаться предложением AND \<clause_search_condition>. Для любой выбранной строки второе предложение WHEN NOT MATCHED BY SOURCE применяется только в тех случаях, если не применяется первое. Если имеется два предложения WHEN NOT MATCHED BY SOURCE, то одно должно указывать действие UPDATE, а другое — действие DELETE. В условии \<clause_search_condition> можно ссылаться только на столбцы целевой таблицы.  
  
 Если строки не возвращаются таблицей \<table_source>, к столбцам в исходной таблице не может быть предоставлен доступ. Если операция обновления или удаления, указанная в предложении \<merge_matched>, ссылается на столбцы исходной таблицы, то возвращается ошибка 207 (недопустимое имя столбца). Например, предложение `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` может стать причиной ошибки инструкции из-за недоступности столбца `Col1` в исходной таблице.  
  
 AND \<clause_search_condition>  
 Указывается любое действительное условие поиска. Дополнительные сведения см. в разделе [Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md).  
  
 \<table_hint_limited>  
 Задается одно или несколько табличных указаний, применяемых в целевой таблице для каждой операции вставки, обновления или удаления, которые выполняются инструкцией MERGE. Ключевое слово WITH и круглые скобки обязательны.  
  
 Использование ключевых слов NOLOCK и READUNCOMMITTED запрещено. Дополнительные сведения о табличных указаниях см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Указание подсказки TABLOCK для целевой таблицы инструкции INSERT приведет к тем же последствиям, что и указание подсказки TABLOCKX. К таблице будет применена монопольная блокировка. Если указано FORCESEEK, то оно применяется к неявному экземпляру целевой таблицы, соединенной с исходной таблицей.  
  
> [!CAUTION]  
>  Указание READPAST с предложением WHEN NOT MATCHED [ BY TARGET ] THEN INSERT может привести к выполнению операций INSERT, которые нарушают ограничения UNIQUE.  
  
 INDEX ( index_val [ ,...n ] )  
 Указывается имя или идентификатор одного или нескольких индексов целевой таблицы для выполнения явного соединения с исходной таблицей. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 \<output_clause>  
 Возвращает по одной строке для каждой строки в *target_table*, с которой выполнена операция обновления, вставки или удаления, без какого-либо определенного порядка. Параметр **$action** может быть указан в предложении вывода. **$action** — это столбец типа **nvarchar(10)**, который возвращает одно из трех значений для каждой строки: INSERT, UPDATE или DELETE — согласно действию, которое было выполнено с этой строкой. Дополнительные сведения об аргументах этого предложения см. в статье [Предложение OUTPUT (Transact-SQL)](../../t-sql/queries/output-clause-transact-sql.md).  
  
 OPTION ( \<query_hint> [ ,...n ] )  
 Указывает, что для настройки способа, которым компонент Database Engine обрабатывает инструкцию, используются подсказки оптимизатора. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
 \<merge_matched>  
 Указывает действие обновления или удаления, которое применяется ко всем строкам *target_table*, не соответствующим строкам, возвращенным \<table_source> ON \<merge_search_condition>, и удовлетворяющим дополнительным условиям поиска.  
  
 UPDATE SET \<set_clause>  
 Указывается список имен столбцов или переменных, которые необходимо обновить в целевой таблице, и значений, которые необходимо использовать для их обновления.  
  
 Дополнительные сведения об аргументах этого предложения см. в разделе [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md). Присваивание переменной того же значения, что и столбцу, не разрешается.  
  
 DELETE  
 Указывает, что строки, совпадающие со строками в *target_table*, удаляются.  
  
 \<merge_not_matched>  
 Указываются значения для вставки в целевую таблицу.  
  
 (*column_list*)  
 Список, состоящий из одного или нескольких столбцов целевой таблицы, в которые вставляются данные. Столбцы необходимо указывать в виде однокомпонентного имени, так как в противном случае инструкция MERGE возвращает ошибку. Список *column_list* должен быть заключен в круглые скобки, а его элементы должны разделяться запятыми.  
  
 VALUES ( *values_list*)  
 Список с разделителями-запятыми констант, переменных или выражений, которые возвращают значения для вставки в целевую таблицу. Выражения не могут содержать инструкцию EXECUTE.  
  
 DEFAULT VALUES  
 Заполняет вставленную строку значениями по умолчанию, определенными для каждого столбца.  
  
 Дополнительные сведения об этом предложении см. в разделе [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).  
  
 \<search condition>  
 Указываются условия поиска, используемые для указания \<merge_search_condition> или \<clause_search_condition>. Дополнительные сведения об аргументах этого предложения см. в разделе [Условия поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md).  

 \<graph search pattern>  
 Определяет шаблон сопоставления графов. Дополнительные сведения об аргументах этого предложения см. в статье [MATCH &#40;Transact-SQL&#41;](../../t-sql/queries/match-sql-graph.md).
  
## <a name="remarks"></a>Remarks  
 Должно быть указано по крайней мере одно из трех предложений MATCHED, но они могут быть указаны в любом порядке. В одном предложении MATCHED переменная не может быть обновлена больше одного раза.  
  
 На все операции удаления, вставки или обновления, указанные применительно к целевой таблице инструкции MERGE, распространяются все ограничения, определенные для этой таблицы, включая все каскадные ограничения ссылочной целостности. Если IGNORE_DUP_KEY имеет значение ON для всех уникальных индексов в целевой таблице, то в инструкции MERGE этот параметр не учитывается.  
  
 Чтобы использовать инструкцию MERGE, необходима точка с запятой (;) как признак конца инструкции. Возникает ошибка 10713, если инструкция MERGE выполняется без признака конца конструкции.  
  
 Если функция [@@ROWCOUNT (Transact-SQL)](../../t-sql/functions/rowcount-transact-sql.md) используется после инструкции MERGE, она возвращает общее количество вставленных, обновленных и удаленных строк из клиента.  
  
 Ключевое слово MERGE полностью резервируется, если установлен уровень совместимости базы данных 100 или выше. Инструкция MERGE доступна при уровне совместимости 90 и 100, однако это ключевое слово не полностью зарезервировано при уровне совместимости 90.  
  
 Инструкцию **MERGE** не следует применять при использовании репликации, обновляемой посредством очередей. Инструкция **MERGE** и обновляемый посредством очередей триггер несовместимы. Замените инструкцию **MERGE** на инструкцию вставки или обновления.  
  
## <a name="trigger-implementation"></a>Реализация триггера  
 Для каждой операции вставки, обновления или удаления, указанной в инструкции MERGE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускает все соответствующие триггеры AFTER, определенные для целевой таблицы, но не гарантирует определенного порядка их запуска. Триггеры, которые определены для одного и того же действия, реализуются в порядке, указанном пользователем. Дополнительные сведения о настройке порядка выполнения триггеров см. в разделе [Указание первого и последнего триггеров](../../relational-databases/triggers/specify-first-and-last-triggers.md).  
  
 Если в целевой таблице включен триггер INSTEAD OF для операций вставки, обновления или удаления, выполняемых инструкцией MERGE, то должен быть включен триггер INSTEAD OF для всех операций, указанных в инструкции MERGE.  
  
 Если в таблице *target_table* определены триггеры INSTEAD OF UPDATE или INSTEAD OF DELETE, то операции обновления или удаления не выполняются. Вместо этого запускаются триггеры, а таблицы **inserted** и **deleted** заполняются соответствующим образом.  
  
 Если в таблице *target_table* определены триггеры INSTEAD OF INSERT, то операции вставки не выполняются. Вместо этого запускаются триггеры, и таблица **inserted** заполняется соответствующим образом.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для исходной таблицы и разрешения INSERT, UPDATE или DELETE для целевой таблицы. Дополнительные сведения см. в подразделе "Разрешения" разделов [SELECT](../../t-sql/queries/select-transact-sql.md), [INSERT](../../t-sql/statements/insert-transact-sql.md), [UPDATE](../../t-sql/queries/update-transact-sql.md) и [DELETE](../../t-sql/statements/delete-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-merge-to-perform-insert-and-update-operations-on-a-table-in-a-single-statement"></a>A. Использование инструкции MERGE для выполнения операций INSERT и UPDATE над таблицей в одной инструкции  
 Чаще всего производится обновление одного или нескольких столбцов в таблице, если существуют совпадающие строки либо вставка данных в новую строку, если совпадающих строк не существует. Это обычно выполняется путем передачи параметров хранимой процедуре, содержащей подходящие инструкции UPDATE и INSERT. Используя инструкцию MERGE, обе эти задачи можно реализовать в одной инструкции. В следующем примере показывается хранимая процедура в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], содержащая инструкции INSERT и UPDATE. Затем процедура изменяется для выполнения эквивалентных операций с использованием единственной инструкции MERGE.  
  
```sql  
CREATE PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
-- Update the row if it exists.      
    UPDATE Production.UnitMeasure  
SET Name = @Name  
WHERE UnitMeasureCode = @UnitMeasureCode  
-- Insert the row if the UPDATE statement failed.  
IF (@@ROWCOUNT = 0 )  
BEGIN  
    INSERT INTO Production.UnitMeasure (UnitMeasureCode, Name)  
    VALUES (@UnitMeasureCode, @Name)  
END  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Test Value';  
SELECT UnitMeasureCode, Name FROM Production.UnitMeasure  
WHERE UnitMeasureCode = 'ABC';  
GO  
  
-- Rewrite the procedure to perform the same operations using the 
-- MERGE statement.  
-- Create a temporary table to hold the updated or inserted values 
-- from the OUTPUT clause.  
CREATE TABLE #MyTempTable  
    (ExistingCode nchar(3),  
     ExistingName nvarchar(50),  
     ExistingDate datetime,  
     ActionTaken nvarchar(10),  
     NewCode nchar(3),  
     NewName nvarchar(50),  
     NewDate datetime  
    );  
GO  
ALTER PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
  
    MERGE Production.UnitMeasure AS target  
    USING (SELECT @UnitMeasureCode, @Name) AS source (UnitMeasureCode, Name)  
    ON (target.UnitMeasureCode = source.UnitMeasureCode)  
    WHEN MATCHED THEN   
        UPDATE SET Name = source.Name  
WHEN NOT MATCHED THEN  
    INSERT (UnitMeasureCode, Name)  
    VALUES (source.UnitMeasureCode, source.Name)  
    OUTPUT deleted.*, $action, inserted.* INTO #MyTempTable;  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'New Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'XYZ', @Name = 'Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Another Test Value';  
  
SELECT * FROM #MyTempTable;  
-- Cleanup   
DELETE FROM Production.UnitMeasure WHERE UnitMeasureCode IN ('ABC','XYZ');  
DROP TABLE #MyTempTable;  
GO  
```  
  
### <a name="b-using-merge-to-perform-update-and-delete-operations-on-a-table-in-a-single-statement"></a>Б. Использование инструкции MERGE для выполнения операций UPDATE и DELETE над таблицей в одной инструкции  
 В следующем примере инструкция MERGE используется для ежедневного обновления таблицы `ProductInventory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] на основе заказов, обработанных в таблице `SalesOrderDetail`. Столбец `Quantity` таблицы `ProductInventory` обновляется путем вычитания количества заказов на каждый продукт, которые размещаются в течение дня в таблице `SalesOrderDetail`. Если количество заказов на продукт таково, что уровень запасов продукта опускается до нуля или становится еще ниже, то строка этого продукта удаляется из таблицы `ProductInventory`.  
  
```sql  
CREATE PROCEDURE Production.usp_UpdateInventory  
    @OrderDate datetime  
AS  
MERGE Production.ProductInventory AS target  
USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
    JOIN Sales.SalesOrderHeader AS soh  
    ON sod.SalesOrderID = soh.SalesOrderID  
    AND soh.OrderDate = @OrderDate  
    GROUP BY ProductID) AS source (ProductID, OrderQty)  
ON (target.ProductID = source.ProductID)  
WHEN MATCHED AND target.Quantity - source.OrderQty <= 0  
    THEN DELETE  
WHEN MATCHED   
    THEN UPDATE SET target.Quantity = target.Quantity - source.OrderQty,   
                    target.ModifiedDate = GETDATE()  
OUTPUT $action, Inserted.ProductID, Inserted.Quantity, 
    Inserted.ModifiedDate, Deleted.ProductID,  
    Deleted.Quantity, Deleted.ModifiedDate;  
GO  
  
EXECUTE Production.usp_UpdateInventory '20030501'  
```  
  
### <a name="c-using-merge-to-perform-update-and-insert-operations-on-a-target-table-by-using-a-derived-source-table"></a>В. Использование инструкции MERGE для выполнения операций UPDATE и INSERT применительно к целевой таблице с помощью производной исходной таблицы  
 В следующем примере инструкция MERGE используется для изменения таблицы `SalesReason` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] путем обновления или вставки строк. Если значение `NewName` в исходной таблице соответствует значению в столбце `Name` целевой таблицы (`SalesReason`), то в целевой таблице обновляется столбец `ReasonType`. Если значение `NewName` не совпадает со значением в целевой таблице, исходная строка вставляется в целевую таблицу. Исходной таблицей является производная таблица, в которой используется конструктор табличных значений [!INCLUDE[tsql](../../includes/tsql-md.md)] для указания нескольких строк исходной таблицы. Дополнительные сведения об использовании конструктора табличных значений в производной таблице см. в разделе [Конструктор табличных значений (Transact-SQL)](../../t-sql/queries/table-value-constructor-transact-sql.md). В примере также показано, как сохранить результаты предложения OUTPUT в табличной переменной, а затем составить сводку результатов инструкцию MERGE, выполняя простую операцию выборки, которая возвращает количество вставленных и обновленных строк.  
  
```sql  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), 
              ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
```  
  
### <a name="d-inserting-the-results-of-the-merge-statement-into-another-table"></a>Г. Вставка результатов инструкции MERGE в другую таблицу  
 В следующем примере производится отслеживание данных, возвращаемых предложением OUTPUT инструкции MERGE, а затем осуществляется вставка этих данных в другую таблицу. В инструкции MERGE ежедневно обновляется столбец `Quantity` таблицы `ProductInventory` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] на основе заказов, обработанных в таблице `SalesOrderDetail`. В этом примере производится отслеживание обновляемых строк и их вставка в другую таблицу, которая используется для отслеживания изменений запасов.  
  
```sql  
CREATE TABLE Production.UpdatedInventory  
    (ProductID INT NOT NULL, LocationID int, NewQty int, PreviousQty int,  
     CONSTRAINT PK_Inventory PRIMARY KEY CLUSTERED (ProductID, LocationID));  
GO  
INSERT INTO Production.UpdatedInventory  
SELECT ProductID, LocationID, NewQty, PreviousQty   
FROM  
(    MERGE Production.ProductInventory AS pi  
     USING (SELECT ProductID, SUM(OrderQty)   
            FROM Sales.SalesOrderDetail AS sod  
            JOIN Sales.SalesOrderHeader AS soh  
            ON sod.SalesOrderID = soh.SalesOrderID  
            AND soh.OrderDate BETWEEN '20030701' AND '20030731'  
            GROUP BY ProductID) AS src (ProductID, OrderQty)  
     ON pi.ProductID = src.ProductID  
    WHEN MATCHED AND pi.Quantity - src.OrderQty >= 0   
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0   
        THEN DELETE  
    OUTPUT $action, Inserted.ProductID, Inserted.LocationID, 
        Inserted.Quantity AS NewQty, Deleted.Quantity AS PreviousQty)  
 AS Changes (Action, ProductID, LocationID, NewQty, PreviousQty) 
 WHERE Action = 'UPDATE';  
GO  
```  

### <a name="e-using-merge-to-perform-insert-or-update-on-a-target-edge-table-in-a-graph-database"></a>Д. Выполнение инструкции INSERT или UPDATE в целевой таблице ребер базы данных графа с помощью MERGE
В этом примере мы создадим таблицы узлов `Person` и `City` и таблицу ребер `livesIn`. Если ребро не определено между таблицами `Person` и `City`, мы вставим новую строку с помощью инструкции MERGE в таблице ребер `livesIn`. Если ребро уже определено, мы только обновим атрибут StreetAddress в таблице ребер `livesIn`.

```sql
-- CREATE node and edge tables
CREATE TABLE Person
    (
        ID INTEGER PRIMARY KEY, 
        PersonName VARCHAR(100)
    )
AS NODE
GO

CREATE TABLE City
    (
        ID INTEGER PRIMARY KEY, 
        CityName VARCHAR(100), 
        StateName VARCHAR(100)
    )
AS NODE
GO

CREATE TABLE livesIn
    (
        StreetAddress VARCHAR(100)
    )
AS EDGE
GO

-- INSERT some test data into node and edge tables
INSERT INTO Person VALUES (1, 'Ron'), (2, 'David'), (3, 'Nancy')
GO

INSERT INTO City VALUES (1, 'Redmond', 'Washington'), (2, 'Seattle', 'Washington')
GO

INSERT livesIn SELECT P.$node_id, C.$node_id, c
FROM Person P, City C, (values (1,1, '123 Avenue'), (2,2,'Main Street')) v(a,b,c)
WHERE P.id = a AND C.id = b
GO

-- Use MERGE to update/insert edge data
CREATE OR ALTER PROCEDURE mergeEdge
    @PersonId integer,
    @CityId integer,
    @StreetAddress varchar(100)
AS
BEGIN
    MERGE livesIn
        USING ((SELECT @PersonId, @CityId, @StreetAddress) AS T (PersonId, CityId, StreetAddress)
                JOIN Person ON T.PersonId = Person.ID
                JOIN City ON T.CityId = City.ID)
        ON MATCH (Person-(livesIn)->City)
    WHEN MATCHED THEN
        UPDATE SET StreetAddress = @StreetAddress
    WHEN NOT MATCHED THEN
        INSERT ($from_id, $to_id, StreetAddress)
        VALUES (Person.$node_id, City.$node_id, @StreetAddress) ;
END
GO

-- Following will insert a new edge in the livesIn edge table
EXEC mergeEdge 3, 2, '4444th Avenue'
GO

-- Following will update the StreetAddress on the edge that connects Ron to Redmond
EXEC mergeEdge 1, 1, '321 Avenue'
GO

-- Verify that all the address were added/updated correctly
SELECT PersonName, CityName, StreetAddress
FROM Person , City , livesIn 
WHERE MATCH(Person-(livesIn)->city)
GO
```
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [Предложение OUTPUT (Transact-SQL)](../../t-sql/queries/output-clause-transact-sql.md)   
 [Предложение MERGE в пакетах служб Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [Конструктор табличных значений (Transact-SQL)](../../t-sql/queries/table-value-constructor-transact-sql.md)  
  
  

