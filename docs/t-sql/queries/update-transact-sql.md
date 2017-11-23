---
title: "UPDATE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE_TSQL
- UPDATE
dev_langs: TSQL
helpviewer_keywords:
- DML [SQL Server], UPDATE statement
- data updates [SQL Server], UPDATE statement
- updating data [SQL Server]
- TOP clause, UPDATE
- OUTPUT clause
- large value data types
- data manipulation language [SQL Server], UPDATE statement
- user-defined types [SQL Server], modifying
- INSTEAD OF triggers
- modifying data [SQL Server], UPDATE statement
- data modifications [SQL Server], UPDATE statement
- large data, modifying
- .WRITE clause
- table modifications [SQL Server], UPDATE statement
- UDTs [SQL Server], modifying
- UPDATE statement [SQL Server], about UPDATE statement
- LOB data [SQL Server], modifying
- modifying LOB data
- UPDATE statement [SQL Server]
- FROM clause, UPDATE statement
- WHERE clause, UPDATE statement
ms.assetid: 40e63302-0c68-4593-af3e-6d190181fee7
caps.latest.revision: "91"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 671eb95a5c1772ec790886d923112d491bbd2a35
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="update-transact-sql"></a>UPDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет существующие данные в таблице или представлении в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Примеры см. в разделе [примеры](#UpdateExamples).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
-- Syntax for SQL Server and Azure SQL Database  

[ WITH <common_table_expression> [...n] ]  
UPDATE   
    [ TOP ( expression ) [ PERCENT ] ]   
    { { table_alias | <object> | rowset_function_limited   
         [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
      }  
      | @table_variable      
    }  
    SET  
        { column_name = { expression | DEFAULT | NULL }  
          | { udt_column_name.{ { property_name = expression  
                                | field_name = expression }  
                                | method_name ( argument [ ,...n ] )  
                              }  
          }  
          | column_name { .WRITE ( expression , @Offset , @Length ) }  
          | @variable = expression  
          | @variable = column = expression  
          | column_name { += | -= | *= | /= | %= | &= | ^= | |= } expression  
          | @variable { += | -= | *= | /= | %= | &= | ^= | |= } expression  
          | @variable = column { += | -= | *= | /= | %= | &= | ^= | |= } expression  
        } [ ,...n ]   
  
    [ <OUTPUT Clause> ]  
    [ FROM{ <table_source> } [ ,...n ] ]   
    [ WHERE { <search_condition>   
            | { [ CURRENT OF   
                  { { [ GLOBAL ] cursor_name }   
                      | cursor_variable_name   
                  }   
                ]  
              }  
            }   
    ]   
    [ OPTION ( <query_hint> [ ,...n ] ) ]  
[ ; ]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
    | database_name .[ schema_name ] .   
    | schema_name .  
    ]  
    table_or_view_name}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

UPDATE [ database_name . [ schema_name ] . | schema_name . ] table_name   
SET { column_name = { expression | NULL } } [ ,...n ]  
[ FROM from_clause ]  
[ WHERE <search_condition> ]   
[ OPTION ( LABEL = label_name ) ]  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 С \<общее_табличное_выражение >  
 Задает временный именованный результирующий набор или представление, которые называются обобщенным табличным выражением (CTE), определяемым в пределах области действия инструкции UPDATE. Результирующий набор CTE, на который ссылается инструкция UPDATE, является производным простого запроса.  
  
 Обобщенные табличные выражения могут также использоваться с инструкциями SELECT, INSERT, DELETE и CREATE VIEW. Дополнительные сведения см. в разделе [с общее_табличное_выражение &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 Начало **(** *выражение***)** [%]  
 Указывает количество или процент строк, которые обновляются. *expression* может быть либо числом, либо процентом от числа строк.  
  
 Строки, на которые ссылается выражение TOP, используемое с инструкциями INSERT, UPDATE и DELETE, не упорядочиваются.  
  
 Разделение круглыми скобками *выражение* необходимые в предложении TOP в инструкциях INSERT, UPDATE и DELETE. Дополнительные сведения см. в разделе [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 *table_alias*  
 Псевдоним, заданный в предложении FROM и представляющий таблицу или представление, строки которых будут обновлены.  
  
 *имя_сервера*  
 Имя сервера (с использованием имени связанного сервера или [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) работать в качестве имени сервера) на котором расположена таблица или представление. Если *имя_сервера* указано, *имя_базы_данных* и *schema_name* являются обязательными.  
  
 *database_name*  
 Имя базы данных.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица или представление.  
  
 *table_or view_name*  
 Имя таблицы или представления, из которых должны обновляться строки. Представление ссылается *table_or_view_name* должно быть обновляемым и ссылаться ровно одну базовую таблицу в предложении FROM представления. Дополнительные сведения об обновляемых представлениях см. в разделе [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 Либо [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) или [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) функции, в зависимости от возможностей поставщика.  
  
 С **(** \<Table_Hint_Limited > **)**  
 Задает одно или несколько табличных указаний, разрешенных для целевой таблицы. Ключевое слово WITH и круглые скобки обязательны. Использование ключевых слов NOLOCK и READUNCOMMITTED запрещено. Сведения о табличных подсказках см. в разделе [табличные подсказки &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 @*table_variable*  
 Указывает [таблицы](../../t-sql/data-types/table-transact-sql.md) переменной в качестве исходной таблицы.  
  
 SET  
 Задает список обновляемых имен столбцов или переменных.  
  
 *column_name*  
 Столбец, содержащий изменяемые данные. *column_name* должен существовать в *table_or view_name*. Столбцы идентификаторов не могут быть обновлены.  
  
 *expression*  
 Переменная, литеральное значение, выражение или инструкция подзапроса выборки (заключенная в скобки), которые возвращают единственное значение. Значение, возвращаемое *выражение* заменяет существующее значение в *column_name* или  *@variable* .  
  
> [!NOTE]  
>  При ссылке на типы данных символов Юникода **nchar**, **nvarchar**, и **ntext**, «выражение» должно начинаться с заглавной буквы 'N'. Если префикс «N» не указан, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнит преобразование строки в кодовую страницу, соответствующую параметрам сортировки базы данных или столбца, действующим по умолчанию. Любые символы, не входящие в эту кодовую страницу, будут утрачены.  
  
 DEFAULT  
 Указывает, что существующее в столбце значение будет заменено значением по умолчанию, определенным для данного столбца. Также может использоваться для присвоения значения NULL, если столбец не имеет значений по умолчанию и может принимать значения NULL.  
  
 { **+=** | **-=** | **\*=** | **/=** | **%=** | **&=** | **^=** | **|=** }  
 Составной оператор присваивания:  
 += Сложение и присваивание  
 -= Вычитание и присваивание  
 * = Умножение и присваивание  
 / = Деление и присваивание  
 % = Остаток от деления и присваивание  
 & = выполнить побитовое и и присвоить  
 ^ = Выполнить побитовое исключающее или и присвоить  
 | = Побитовое или и присвоить  
  
 *udt_column_name*  
 Столбец определяемого пользователем типа.  
  
 *property_name* | *имя_поля*  
 Общедоступное свойство или общедоступный элемент данных определяемого пользоватлем типа.  
  
 *имя_метода* **(** *аргумент* [ **,**... *n*] **)**  
 Метод общего мутатора *udt_column_name* , принимающий один или несколько аргументов.  
  
 **.** Записи **(***выражение***,***@Offset***,** *@Length***)**  
 Указывает, что раздел значение *column_name* подлежит изменению. *выражение* заменяет  *@Length*  элементы, начиная с  *@Offset*  из *column_name*. Только столбцы **varchar(max)**, **nvarchar(max)**, или **varbinary(max)** можно указать с помощью этого предложения. *column_name* не может иметь значение NULL и не может быть дополнены именем таблицы или псевдонимом таблицы.  
  
 *выражение* является значением, которое копируется в *column_name*. *выражение* должен преобразовываться или может быть неявно приведен к *column_name* типа. Если *выражение* имеет значение NULL,  *@Length*  игнорируется, а значение в *column_name* усекается по указанному индексу  *@Offset* .  
  
 *@Offset*является отправной точкой в значении *column_name* скорость *выражение* записывается. *@Offset*Отсчитываемый от нуля порядковый номер является, **bigint**, и не может быть отрицательным числом. Если  *@Offset*  имеет значение NULL, операция обновления добавляет *выражение* в конце существующего *column_name* значение и  *@Length*  учитывается. Если @Offset больше, чем длина *column_name* значение, [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает сообщение об ошибке. Если  *@Offset*  , а также  *@Length*  превышает длину базового значения столбца, удаление выполняется до до последнего знака значения. Если  *@Offset*  плюс длина (*выражение*) больше, чем базовый объявленный размер, возникает ошибка.  
  
 *@Length*— это длина раздела в столбце, начиная с  *@Offset* , который заменяется *выражение*. *@Length*— **bigint** и не может быть отрицательным числом. Если  *@Length*  имеет значение NULL, операция обновления удаляет все данные из  *@Offset*  в конец *column_name* значение.  
  
 Дополнительные сведения см. в подразделе «Примечания».  
  
 **@***переменной*  
 Объявленная переменная, которой присваивается значение, возвращаемое *выражение*.  
  
 ЗАДАТЬ  **@**  *переменной* = *столбца* = *выражение* задает переменную с тем же значение в виде столбца. Это отличается от НАБОРА  **@**  *переменной* = *столбца*, *столбца*  =  *выражение*, который присваивает переменной значение столбца перед обновлением.  
  
 \<OUTPUT_Clause >  
 Возвращает обновленные данные или основанные на них выражения в рамках выполнения операции UPDATE. Предложение OUTPUT не поддерживается ни в одной инструкции DML, целью которой являются удаленные таблицы или представления. Дополнительные сведения см. в разделе [предложение OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
 ИЗ \<table_source >  
 Определяет, что для определения критериев операции обновления используется таблица, представление или производная таблица. Дополнительные сведения см. в разделе [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  
  
 Если обновляемый объект совпадает с объектом в предложении FROM, а в предложении FROM имеется только одна ссылка на этот объект, псевдоним объекта указывать не обязательно. Если обновляемый объект встречается в предложении FROM несколько раз, одна и только одна ссылка на этот объект не должна указывать псевдоним таблицы. Все остальные ссылки на объект в предложении FROM должны включать псевдоним объекта.  
  
 Представление с триггером INSTEAD OF UPDATE не может быть целью инструкции UPDATE с предложением FROM.  
  
> [!NOTE]  
>  Любой вызов функции OPENDATASOURCE, OPENQUERY или OPENROWSET в предложении FROM вычисляется отдельно и независимо от любого вызова этих функций, используемого как назначение при обновлении, даже если в двух таких вызовах будут заданы идентичные аргументы. В частности, условия фильтра или соединения, применяемые к результатам одного из таких вызовов, никак не влияют на результаты другого.  
  
 WHERE  
 Задает условия, ограничивающие обновляемые строки. Существует два вида обновлений в зависимости от используемой формы предложения WHERE.  
  
-   В поисковых обновлениях задается условие поиска строк, предназначенных к удалению.  
  
-   В позиционных обновлениях используется предложение CURRENT OF для указания курсора. Операция обновления выполняется в текущем положении курсора.  
  
\<search_condition >  
 Задает условие, которому должны удовлетворять обновляемые строки. Условие поиска может также представлять собой условие, на котором основано соединение. Количество предикатов, которое может содержать условие поиска, не ограничено. Дополнительные сведения о предикатах и условиях поиска см. в разделе [условие поиска &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
CURRENT OF  
 Определяет, что обновление выполняется в текущей позиции указанного курсора.  
  
 Позиционированное обновление с использованием предложения WHERE CURRENT OF обновляет единственную строку в текущем положении курсора. Это может быть более точной, чем поисковое обновление, использующая предложение WHERE \<search_condition > предложения для уточнения обновляемые строки. Если условие поиска не определяет однозначно единственную строку, поисковое обновление изменяет несколько строк.  
  
GLOBAL  
 Указывает, что *cursor_name* ссылается на глобальный курсор.  
  
*cursor_name*  
 Имя открытого курсора, из которого должна быть произведена выборка. Если как глобальный, так и локальный курсор с именем *cursor_name* существует, этот аргумент ссылается на глобальный курсор, если GLOBAL указанного; в противном случае, он ссылается на локальный курсор. Курсор должен позволять производить обновления.  
  
*cursor_variable_name*  
 Имя переменной курсора. *cursor_variable_name* должен ссылаться на курсор, обновления которого разрешены.  
  
ПАРАМЕТР **(** \<query_hint > [ **,**... *n* ] **)**  
 Определяет, что для настройки способа, которым компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] обрабатывает инструкцию, используются подсказки оптимизатора. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
## <a name="best-practices"></a>Рекомендации  
 Используйте @@ROWCOUNT функция возвращает количество вставленных строк клиентскому приложению. Дополнительные сведения см. в разделе [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md).  
  
 В инструкции UPDATE можно использовать имена переменных для показа старых и новых значений, но только в том случае, если инструкция UPDATE обрабатывает одну запись. Если инструкция UPDATE затрагивает несколько записей, для возвращения старых и новых значений каждой записи используйте [предложение OUTPUT](../../t-sql/queries/output-clause-transact-sql.md).  
  
 Проявляйте осторожность, указывая предложение FROM при задании критериев для операции обновления. Результаты инструкции UPDATE не определены, если инструкция включает предложение FROM, в котором для каждого вхождения обновляемого столбца не задано единственное значение, то есть если инструкция UPDATE не является детерминированной. Например, в инструкции UPDATE следующего скрипта обе строки в `Table1` удовлетворяют условиям предложения FROM в инструкции UPDATE, но не определено, какая строка из `Table1` используется для обновления строки в `Table2.`  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('dbo.Table1', 'U') IS NOT NULL  
    DROP TABLE dbo.Table1;  
GO  
IF OBJECT_ID ('dbo.Table2', 'U') IS NOT NULL  
    DROP TABLE dbo.Table2;  
GO  
CREATE TABLE dbo.Table1   
    (ColA int NOT NULL, ColB decimal(10,3) NOT NULL);  
GO  
CREATE TABLE dbo.Table2   
    (ColA int PRIMARY KEY NOT NULL, ColB decimal(10,3) NOT NULL);  
GO  
INSERT INTO dbo.Table1 VALUES(1, 10.0), (1, 20.0);  
INSERT INTO dbo.Table2 VALUES(1, 0.0);  
GO  
UPDATE dbo.Table2   
SET dbo.Table2.ColB = dbo.Table2.ColB + dbo.Table1.ColB  
FROM dbo.Table2   
    INNER JOIN dbo.Table1   
    ON (dbo.Table2.ColA = dbo.Table1.ColA);  
GO  
SELECT ColA, ColB   
FROM dbo.Table2;  
```  
  
 То же самое может произойти при сочетании предложений FROM и WHERE CURRENT OF. В следующем примере обе строки в `Table2` удовлетворяют условиям предложения `FROM` в инструкции `UPDATE`. Не определено, какая строка из `Table2` должна использоваться для обновления строки в `Table1`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('dbo.Table1', 'U') IS NOT NULL  
    DROP TABLE dbo.Table1;  
GO  
IF OBJECT_ID ('dbo.Table2', 'U') IS NOT NULL  
    DROP TABLE dbo.Table2;  
GO  
CREATE TABLE dbo.Table1  
    (c1 int PRIMARY KEY NOT NULL, c2 int NOT NULL);  
GO  
CREATE TABLE dbo.Table2  
    (d1 int PRIMARY KEY NOT NULL, d2 int NOT NULL);  
GO  
INSERT INTO dbo.Table1 VALUES (1, 10);  
INSERT INTO dbo.Table2 VALUES (1, 20), (2, 30);  
GO  
DECLARE abc CURSOR LOCAL FOR  
    SELECT c1, c2   
    FROM dbo.Table1;  
OPEN abc;  
FETCH abc;  
UPDATE dbo.Table1   
SET c2 = c2 + d2   
FROM dbo.Table2   
WHERE CURRENT OF abc;  
GO  
SELECT c1, c2 FROM dbo.Table1;  
GO  
```  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 Поддержка использования подсказок READUNCOMMITTED и NOLOCK в предложении FROM, применяемом к целевой таблице инструкции UPDATE или DELETE, будет удалена в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует избегать использования этих указаний в таком контексте в новой разработке и запланировать изменение приложений, использующих их в настоящий момент.  
  
## <a name="data-types"></a>Типы данных  
 Все **char** и **nchar** столбцы заполняются вправо до заданной длины.  
  
 Если ANSI_PADDING имеет значение OFF, все конечные пробелы удаляются из данных, вставленных в **varchar** и **nvarchar** столбцы, за исключением строк, содержащих только пробелы. Эти строки усекаются до пустых строк. Если ANSI_PADDING имеет значение ON, вставляются конечные пробелы. Драйвер ODBC для Microsoft SQL Server и поставщик OLE DB для SQL Server автоматически устанавливают ANSI_PADDING ON для каждого соединения. Этот параметр можно настроить в источниках данных ODBC или устанавливая атрибуты или свойства соединений. Дополнительные сведения см. в разделе [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
### <a name="updating-text-ntext-and-image-columns"></a>Обновление столбцов типа text, ntext и image  
 Изменение **текст**, **ntext**, или **изображение** с помощью инструкции UPDATE инициализирует столбец, присваивает ему допустимый текстовый указатель и выделяет по крайней мере одну страницу данных, если выполняется обновление столбцов со значением NULL.  
  
 Чтобы заменить или изменить большие блоки **текст**, **ntext**, или **изображения** данных, использовать [WRITETEXT](../../t-sql/queries/writetext-transact-sql.md) или [UPDATETEXT](../../t-sql/queries/updatetext-transact-sql.md) вместо инструкции UPDATE.  
  
 Если инструкция UPDATE могла обновить несколько строк при обновлении как ключа кластеризации и один или несколько **текст**, **ntext**, или **изображения** столбцов, то частичное обновление этих столбцов выполняется как полная замена значений.  
  
> [!IMPORTANT]  
>  **Ntext**, **текст**, и **изображения** типов данных будет удалена в будущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует избегать использования этих типов данных при новой разработке и запланировать изменение приложений, использующих их в настоящий момент. Вместо них следует использовать типы данных [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)и [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) .  
  
### <a name="updating-large-value-data-types"></a>Обновление типов данных большого объема  
 Используйте **.** ЗАПИСЬ (*выражение***,**  *@Offset*  **,***@Length*) предложения выполнить частичное или полное обновление **varchar(max)**, **nvarchar(max)**, и **varbinary(max)** типов данных. Например, частичное обновление **varchar(max)** столбца может удалить или изменить только первые 200 символов столбца, тогда как полное обновление удалит или изменит все данные в столбце. **.** Записи, обновления, вставки или добавления новых данных регистрируются на минимальном уровне Если с неполным протоколированием или простая модель восстановления базы данных. Если обновляются существующие значения, ведение журнала не сокращается до минимума. Дополнительные сведения см. в статье [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] преобразует частичное обновление в полное, если инструкция UPDATE приводит к одному из следующих действий.  
-   Изменения ключевого столбца секционированного представления или таблицы.  
-   Изменение более одной строки, а также обновление ключа неуникального кластеризованного индекса на непостоянное значение.  
  
Нельзя использовать **.** Write для обновления столбца NULL или задать значение *column_name* значение NULL.  
  
*@Offset*и  *@Length*  указываются в байтах для **varbinary** и **varchar** типов данных и в символах для **nvarchar**тип данных. Соответствующие смещения вычисляются для параметров сортировки в двухбайтовых кодировках (DBCS).  
  
В целях увеличения производительности рекомендуется вставлять или обновлять данные фрагментами, кратными 8040 байтам.  
  
Если столбец, изменяемый предложением **.** WRITE, ссылается предложение OUTPUT, полное значение данного столбца, либо исходный образ в **удалены.** *column_name* или в последующем образе **вставлен.** *column_name*, возвращается к указанному столбцу в табличной переменной. См. в следующем примере R.  
  
Чтобы добиться функциональности предложения **.** ЗАПИСИ с других символьных или двоичных типов данных следует использовать [STUFF &#40; Transact-SQL &#41; ](../../t-sql/functions/stuff-transact-sql.md).  
  
### <a name="updating-user-defined-type-columns"></a>Обновление столбцов определяемого пользователем типа  
 Обновление столбцов определяемого пользователем типа можно выполнить одним из следующих способов.  
  
-   Предоставление значения типа системных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] происходит, если определяемый пользователем тип поддерживает явное или неявное преобразование из этого типа. Следующий пример демонстрирует, как обновить значение в столбце определяемого пользователем типа `Point` путем явного преобразования строки.  
  
    ```sql  
    UPDATE Cities  
    SET Location = CONVERT(Point, '12.3:46.2')  
    WHERE Name = 'Anchorage';  
    ```  
  
-   Вызов метода, помеченного в качестве мутатора определенного пользователем типа для осуществления обновления. Следующий пример вызывает метод мутатора типа `Point` с именем `SetXY`. Это обновляет состояние экземпляра типа.  
  
    ```sql  
    UPDATE Cities  
    SET Location.SetXY(23.5, 23.5)  
    WHERE Name = 'Anchorage';  
    ```  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку, если метод мутатора возвращает значение NULL языка [!INCLUDE[tsql](../../includes/tsql-md.md)] либо если новое значение, порожденное методом мутатора, соответствует значению NULL.  
  
-   Изменение значения зарегистрированного свойства или общедоступного элемента данных определяемого пользователем типа. Выражение, предоставляющее значение, должно допускать неявное преобразование в тип свойства. В следующем примере изменяется значение свойства `X` определяемого пользователем типа `Point`.  
  
    ```sql  
    UPDATE Cities  
    SET Location.X = 23.5  
    WHERE Name = 'Anchorage';  
    ```  
  
     Для изменения различных свойств одного и того же столбца определяемого пользователем типа нужно выполнить несколько инструкций UPDATE или использовать метод мутатора соответствующего типа.  
  
### <a name="updating-filestream-data"></a>Обновление данных FILESTREAM  
 Инструкция UPDATE позволяет обновить поля FILESTREAM значением NULL, пустым значением или встроенными данными относительно небольшого размера. Однако при работе с большими объемами данных более эффективно передавать поток в файл с использованием интерфейсов Win32. При обновлении поля FILESTREAM происходит изменение базовых данных BLOB в файловой системе. Если в поле FILESTREAM содержится значение NULL, данные BLOB, связанные с этим полем, удаляются. Нельзя использовать. Write(), для выполнения частичных обновлений данных FILESTREAM. Дополнительные сведения см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если обновление строки нарушает ограничение, правило или установку NULL для столбца либо новое значение имеет несовместимый тип данных, то инструкция отменяется, возвращается ошибка и никакие записи не обновляются.  
  
 Если инструкция UPDATE при оценке выражения встречает арифметическую ошибку (переполнение, деление на ноль или ошибку домена), обновление не выполняется. Остальная часть пакета не выполняется и возвращается сообщение об ошибке.  
  
 Если обновление столбца или столбцов, участвующих в кластеризованном индексе, приводит к тому, что размер кластеризованного индекса и строки превышает 8 060 байт, обновление заканчивается неудачей и возвращается сообщение об ошибке.  
  
## <a name="interoperability"></a>Совместимость  
 Инструкции UPDATE разрешается использовать в теле определяемых пользователем функций только в том случае, если изменяемая таблица является табличной переменной.  
  
 Если для операций UPDATE по отношению к таблице определен триггер INSTEAD OF, вместо инструкции UPDATE запускается этот триггер. Ранние версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживали для UPDATE и других инструкций изменения данных только определение триггеров AFTER. В инструкции UPDATE, которая прямо или косвенно ссылается на представление с определенным для него триггером INSTEAD OF, не может быть указано предложение FROM. Дополнительные сведения о триггеры INSTEAD OF см. в разделе [CREATE TRIGGER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 В инструкции UPDATE, которая прямо или косвенно ссылается на представление с определенным для него триггером INSTEAD OF, не может быть указано предложение FROM. Дополнительные сведения о триггеры INSTEAD OF см. в разделе [CREATE TRIGGER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
 Если обобщенное табличное выражение указывается в качестве цели инструкции UPDATE, должны совпадать все ссылки на это выражение в инструкции. Например, если для обобщенного табличного выражения в предложении FROM назначается псевдоним, то этот псевдоним должен использоваться для всех остальных ссылок на обобщенное табличное выражение. Требуются ссылки на однозначный обобщенного табличного Выражения, так как обобщенное табличное Выражение не имеет идентификатор объекта, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для распознавания явную связь между объектом и его псевдоним. В отсутствие такой связи план запроса может непредвиденным образом построить работу с соединениями, что приведет к нежелательным результатам запроса. В следующих примерах показаны правильные и неправильные методы задания обобщенного табличного выражения, когда оно является целевым объектом операции обновления.  
  
```sql  
USE tempdb;  
GO  
-- UPDATE statement with CTE references that are correctly matched.  
DECLARE @x TABLE (ID int, Value int);  
DECLARE @y TABLE (ID int, Value int);  
INSERT @x VALUES (1, 10), (2, 20);  
INSERT @y VALUES (1, 100),(2, 200);  
  
WITH cte AS (SELECT * FROM @x)  
UPDATE x -- cte is referenced by the alias.  
SET Value = y.Value  
FROM cte AS x  -- cte is assigned an alias.  
INNER JOIN @y AS y ON y.ID = x.ID;  
SELECT * FROM @x;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ID     Value  
 ------ -----  
 1      100  
 2      200  
 (2 row(s) affected)  
```  

Инструкция UPDATE со ссылками на обобщенное табличное Выражение, которые согласуются с неправильно.  
```sql  
USE tempdb;  
GO  
DECLARE @x TABLE (ID int, Value int);  
DECLARE @y TABLE (ID int, Value int);  
INSERT @x VALUES (1, 10), (2, 20);  
INSERT @y VALUES (1, 100),(2, 200);  
  
WITH cte AS (SELECT * FROM @x)  
UPDATE cte   -- cte is not referenced by the alias.  
SET Value = y.Value  
FROM cte AS x  -- cte is assigned an alias.  
INNER JOIN @y AS y ON y.ID = x.ID;   
SELECT * FROM @x;   
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ID     Value  
------ -----  
1      100  
2      100  
(2 row(s) affected)  
```  

## <a name="locking-behavior"></a>Режим блокировки  
 Инструкция UPDATE всегда получает монопольную блокировку (X) на таблицу, которую она изменяет, и держит блокировку до тех пор, пока транзакция не завершится. При наличии монопольной блокировки другие транзакции не могут изменять данные. Можно переопределить поведение оптимизатора запросов по умолчанию с помощью табличных подсказок на время выполнения инструкции UPDATE указанием другого способа блокировки, но использовать подсказки рекомендуется только опытным разработчикам и администраторам баз данных и только при крайней необходимости. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
## <a name="logging-behavior"></a>Режим ведения журнала  
 Инструкция UPDATE записывается; Однако частичные обновления типов данных больших значений с использованием **.** НАПИШИТЕ предложение регистрируются на минимальном уровне. Дополнительные сведения см. ниже в подразделе «Обновление типов данных большого объема» приведенного ранее раздела «Типы данных».  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуются разрешения на выполнение UPDATE в целевой таблице. Разрешения SELECT также необходимы для обновляемой таблицы, если инструкция UPDATE содержит предложение WHERE или *выражение* в НАБОРЕ предложение используется столбец в таблице.  
  
 ОБНОВИТЬ разрешения по умолчанию для членов **sysadmin** предопределенной роли сервера **db_owner** и **db_datawriter** фиксированной роли базы данных, а также владельцу таблицы. Члены **sysadmin**, **db_owner**, и **db_securityadmin** ролей, а также владелец таблицы могут передавать разрешения другим пользователям.  
  
##  <a name="UpdateExamples"></a> Примеры  
  
|Категория|Используемые элементы синтаксиса|  
|--------------|------------------------------|  
|[Базовый синтаксис](#BasicSyntax)|UPDATE|  
|[Ограничение обновляемых строк](#LimitingValues)|WHERE • TOP • WITH обобщенное табличное выражение • WHERE CURRENT OF|  
|[Задание значений столбцов](#ColumnValues)|вычисляемые значения • составные операторы • значения по умолчанию • вложенные запросы|  
|[Указание целевых объектов, отличных от стандартных таблиц](#TargetObjects)|представления • табличные переменные • псевдонимы таблицы|  
|[Обновление данных на основе данных из других таблиц](#OtherTables)|FROM|  
|[Обновление строк в удаленной таблице](#RemoteTables)|связанный сервер • OPENQUERY • OPENDATASOURCE|  
|[Обновление типов данных больших объектов](#LOBValues)|. • OPENROWSET ЗАПИСИ|  
|[Обновление определяемых пользователем типов](#UDTs)|определяемые пользователем типы|  
|[Переопределение поведения по умолчанию оптимизатор запросов с помощью подсказок](#TableHints)|табличные подсказки • подсказки в запросах|  
|[Сбор результатов инструкции UPDATE](#CaptureResults)|OUTPUT, предложение|  
|[Использование UPDATE в других инструкциях](#Other)|Хранимые процедуры • TRY…CATCH|  
  
###  <a name="BasicSyntax"></a>Базовый синтаксис  
 В примерах в этом разделе описывается базовая функциональность инструкции UPDATE с помощью минимального необходимого синтаксиса.  
  
#### <a name="a-using-a-simple-update-statement"></a>A. Использование простой инструкции UPDATE  
 В следующем примере обновляется один столбец для всех строк в таблице `Person.Address`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Person.Address  
SET ModifiedDate = GETDATE();  
```  
  
#### <a name="b-updating-multiple-columns"></a>Б. Обновление нескольких столбцов  
 В следующем примере выполняется обновление значений в столбцах `Bonus`, `CommissionPct` и `SalesQuota` для всех строк в таблице `SalesPerson`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET Bonus = 6000, CommissionPct = .10, SalesQuota = NULL;  
GO  
```  
  
###  <a name="LimitingValues"></a>Ограничение обновляемых строк  
 В примерах в этом разделе описываются способы ограничения количества строк, на которые влияет инструкция UPDATE.  
  
#### <a name="c-using-the-where-clause"></a>В. Применение предложения WHERE  
 В следующем примере предложение WHERE используется для указания строк, которые необходимо обновить. Инструкция обновляет значение в столбце `Color` таблицы `Production.Product` для всех строк, в которых имеется существующее значение Red в столбце `Color` и имеется значение в столбце `Name`, который начинается с Road-250.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.Product  
SET Color = N'Metallic Red'  
WHERE Name LIKE N'Road-250%' AND Color = N'Red';  
GO  
```  
  
#### <a name="d-using-the-top-clause"></a>Г. Использование предложения TOP  
 В следующем примере предложение TOP используется для ограничения числа строк, изменяемых в процессе выполнения инструкции UPDATE. Когда TOP (*n*) в инструкции UPDATE указано предложение, операция обновления выполняется для произвольного подмножества "*n*" число строк. В следующем примере обновляется `VacationHours` столбца на 25 процентов для 10 случайных строк в `Employee` таблицы.  
  
```sql  
USE AdventureWorks2012;
GO
UPDATE TOP (10) HumanResources.Employee
SET VacationHours = VacationHours * 1.25 ;
GO  
```  
  
 Если нужно применить изменения с предложением TOP в определенной последовательности, укажите во вложенной инструкции выборки инструкцию ORDER BY. В следующем примере изменяется длительность отпуска для 10 сотрудников, имеющих наибольший стаж работы.  
  
```sql  
UPDATE HumanResources.Employee  
SET VacationHours = VacationHours + 8  
FROM (SELECT TOP 10 BusinessEntityID FROM HumanResources.Employee  
     ORDER BY HireDate ASC) AS th  
WHERE HumanResources.Employee.BusinessEntityID = th.BusinessEntityID;  
GO  
```  
  
#### <a name="e-using-the-with-commontableexpression-clause"></a>Д. Использование предложения WITH обобщенное_табличное_выражение  
 В следующем примере обновляется значение `PerAssemnblyQty` для всех частей и компонентов, прямо или косвенно используемых для создания `ProductAssemblyID 800`. Обобщенное табличное выражение возвращает иерархический список частей, которые непосредственно используются для сборки `ProductAssemblyID 800`, и частей, которые используются для сборки этих компонентов, и т. д. Изменяются только строки, возвращенные обобщенным табличным выражением.  
  
```sql  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
UPDATE Production.BillOfMaterials  
SET PerAssemblyQty = c.PerAssemblyQty * 2  
FROM Production.BillOfMaterials AS c  
JOIN Parts AS d ON c.ProductAssemblyID = d.AssemblyID  
WHERE d.ComponentLevel = 0;  
```  
  
#### <a name="f-using-the-where-current-of-clause"></a>Е. Использование предложения WHERE CURRENT OF  
 В следующем примере предложение WHERE CURRENT OF используется только для обновления строк, на которых установлен курсор. Если курсор основан на соединении, изменяется только таблица `table_name`, указанная в инструкции UPDATE. Другие таблицы, участвующие в курсоре, не затрагиваются.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE complex_cursor CURSOR FOR  
    SELECT a.BusinessEntityID  
    FROM HumanResources.EmployeePayHistory AS a  
    WHERE RateChangeDate <>   
         (SELECT MAX(RateChangeDate)  
          FROM HumanResources.EmployeePayHistory AS b  
          WHERE a.BusinessEntityID = b.BusinessEntityID) ;  
OPEN complex_cursor;  
FETCH FROM complex_cursor;  
UPDATE HumanResources.EmployeePayHistory  
SET PayFrequency = 2   
WHERE CURRENT OF complex_cursor;  
CLOSE complex_cursor;  
DEALLOCATE complex_cursor;  
GO  
```  
  
###  <a name="ColumnValues"></a>Задание значений столбцов  
 В примерах этого раздела описывается обновление столбцов с помощью вычисляемых значений, вложенных запросов и значений DEFAULT.  
  
#### <a name="g-specifying-a-computed-value"></a>Ж. Указание вычисляемого значения  
 В следующих примерах используются вычисляемые значения в инструкции UPDATE. В примере удваивается значение столбца `ListPrice` для всех строк в таблице `Product`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
UPDATE Production.Product  
SET ListPrice = ListPrice * 2;  
GO  
```  
  
#### <a name="h-specifying-a-compound-operator"></a>З. Задание составного оператора  
 В следующем примере демонстрируется использование переменной `@NewPrice` для увеличения цены красных велосипедов прибавлением 10 к текущей цене.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @NewPrice int = 10;  
UPDATE Production.Product  
SET ListPrice += @NewPrice  
WHERE Color = N'Red';  
GO  
```  
  
 В следующем примере используется составной оператор += для добавления данных `' - tool malfunction'` к существующему значению в столбце `Name` для строк, имеющих значение `ScrapReasonID` от 10 до 12.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.ScrapReason   
SET Name += ' - tool malfunction'  
WHERE ScrapReasonID BETWEEN 10 and 12;  
```  
  
#### <a name="i-specifying-a-subquery-in-the-set-clause"></a>И. Задание вложенного запроса в предложении SET  
 В следующем примере используется вложенный запрос в предложении SET для определения значения, которое используется для обновления столбца. Вложенный запрос должен возвращать только скалярное значение (то есть одно значение для каждой строки). В примере изменяется столбец `SalesYTD` в таблице `SalesPerson` для отображения самой последней информации о продажах, зафиксированной в таблице `SalesOrderHeader`. Вложенный запрос проводит статистическую обработку сведений о продажах по всем продавцам в инструкции `UPDATE`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET SalesYTD = SalesYTD +   
    (SELECT SUM(so.SubTotal)   
     FROM Sales.SalesOrderHeader AS so  
     WHERE so.OrderDate = (SELECT MAX(OrderDate)  
                           FROM Sales.SalesOrderHeader AS so2  
                           WHERE so2.SalesPersonID = so.SalesPersonID)  
     AND Sales.SalesPerson.BusinessEntityID = so.SalesPersonID  
     GROUP BY so.SalesPersonID);  
GO  
```  
  
#### <a name="j-updating-rows-using-default-values"></a>К. Обновление строк с использованием значений DEFAULT  
 В следующем примере для столбца `CostRate` задается значение по умолчанию (0,00) для всех строк, значение `CostRate` которых больше `20.00`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.Location  
SET CostRate = DEFAULT  
WHERE CostRate > 20.00;  
```  
  
###  <a name="TargetObjects"></a>Указание целевых объектов, отличных от стандартных таблиц  
 В примерах этого раздела описаны методы обновления строк с указанием представления, псевдонима таблицы или табличной переменной.  
  
#### <a name="k-specifying-a-view-as-the-target-object"></a>Л. Указание представления в качестве целевого объекта  
 В следующем примере выполняется обновление строк таблицы путем указания представления в качестве целевого объекта. Определение представления ссылается на несколько таблиц, однако инструкция UPDATE была успешно выполнена, поскольку она ссылается на столбцы только одной из базовых таблиц. При выполнении инструкции UPDATE произойдет сбой, если были указаны столбцы из обеих таблиц. Дополнительные сведения см. в разделе [изменение данных через представление](../../relational-databases/views/modify-data-through-a-view.md).  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Person.vStateProvinceCountryRegion  
SET CountryRegionName = 'United States of America'  
WHERE CountryRegionName = 'United States';  
```  
  
#### <a name="l-specifying-a-table-alias-as-the-target-object"></a>М. Задание псевдонима таблицы в качестве целевого объекта  
 В следующем примере производится обновление строк в таблице `Production.ScrapReason`. Псевдоним таблицы, заданный для `ScrapReason` в предложении FROM, указывается как целевой объект в предложении UPDATE.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE sr  
SET sr.Name += ' - tool malfunction'  
FROM Production.ScrapReason AS sr  
JOIN Production.WorkOrder AS wo   
     ON sr.ScrapReasonID = wo.ScrapReasonID  
     AND wo.ScrappedQty > 300;  
```  
  
#### <a name="m-specifying-a-table-variable-as-the-target-object"></a>Н. Задание табличной переменной в качестве целевого объекта  
 В следующем примере производится обновление строк в табличной переменной.  
  
```sql  
USE AdventureWorks2012;  
GO  
-- Create the table variable.  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    NewVacationHours int,  
    ModifiedDate datetime);  
  
-- Populate the table variable with employee ID values from HumanResources.Employee.  
INSERT INTO @MyTableVar (EmpID)  
    SELECT BusinessEntityID FROM HumanResources.Employee;  
  
-- Update columns in the table variable.  
UPDATE @MyTableVar  
SET NewVacationHours = e.VacationHours + 20,  
    ModifiedDate = GETDATE()  
FROM HumanResources.Employee AS e   
WHERE e.BusinessEntityID = EmpID;  
  
-- Display the results of the UPDATE statement.  
SELECT EmpID, NewVacationHours, ModifiedDate FROM @MyTableVar  
ORDER BY EmpID;  
GO  
```  
  
###  <a name="OtherTables"></a>Обновление данных на основе данных из других таблиц  
 В примерах этого раздела описаны методы обновления строк одной таблицы на основе данных в другой таблице.  
  
#### <a name="n-using-the-update-statement-with-information-from-another-table"></a>О. Использование инструкции UPDATE с данными из другой таблицы  
 В следующем примере изменяется столбец `SalesYTD` в таблице `SalesPerson` для отображения самой последней информации о продажах, зафиксированной в таблице `SalesOrderHeader`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET SalesYTD = SalesYTD + SubTotal  
FROM Sales.SalesPerson AS sp  
JOIN Sales.SalesOrderHeader AS so  
    ON sp.BusinessEntityID = so.SalesPersonID  
    AND so.OrderDate = (SELECT MAX(OrderDate)  
                        FROM Sales.SalesOrderHeader  
                        WHERE SalesPersonID = sp.BusinessEntityID);  
GO  
```  
  
 В предыдущем примере подразумевается, что на конкретного менеджера по продажам на каждую конкретную дату записана только одна продажа и выполнены все текущие обновления. Если в один и тот же день для указанного менеджера может иметься более одной продажи, приведенный пример будет работать неправильно. В этом примере запускается без ошибок, но каждое `SalesYTD` значение обновляется только одна Продажа, независимо от того, каким образом действительного количества продаж в этот день. Это происходит потому, что одиночная инструкция UPDATE никогда не обновляет одну и ту же строку дважды.  
  
 В ситуации, когда у данного менеджера по продажам имеется несколько продаж в день, все продажи для каждого из менеджеров по продажам должны быть собраны вместе инструкцией `UPDATE`, как показано в следующем примере.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET SalesYTD = SalesYTD +   
    (SELECT SUM(so.SubTotal)   
     FROM Sales.SalesOrderHeader AS so  
     WHERE so.OrderDate = (SELECT MAX(OrderDate)  
                           FROM Sales.SalesOrderHeader AS so2  
                           WHERE so2.SalesPersonID = so.SalesPersonID)  
     AND Sales.SalesPerson.BusinessEntityID = so.SalesPersonID  
     GROUP BY so.SalesPersonID);  
GO  
```  
  
###  <a name="RemoteTables"></a>Обновление строк в удаленной таблице  
 Примеры в этом разделе демонстрируют, как для обновления строк в удаленную целевую таблицу с помощью [связанного сервера](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) или [функцию набора строк](../../t-sql/functions/rowset-functions-transact-sql.md) для ссылки на удаленную таблицу.  
  
#### <a name="o-updating-data-in-a-remote-table-by-using-a-linked-server"></a>П. Обновление данных в удаленной таблице с использованием связанного сервера  
 В следующем примере обновляется таблица на удаленном сервере. Пример начинается с создания ссылки на удаленный источник данных с помощью [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Затем имя связанного сервера `MyLinkServer` указывается в качестве одного из четырех компонентов имени объекта в формате сервер.каталог.схема.объект. Обратите внимание, что необходимо указать действительное имя сервера для `@datasrc`.  
  
```sql  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' or 'server_nameinstance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI10',   
    @datasrc = N'<server name>',  
    @catalog = N'AdventureWorks2012';  
GO  
USE AdventureWorks2012;  
GO  
-- Specify the remote data source using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
UPDATE MyLinkServer.AdventureWorks2012.HumanResources.Department  
SET GroupName = N'Public Relations'  
WHERE DepartmentID = 4;  
```  
  
#### <a name="p-updating-data-in-a-remote-table-by-using-the-openquery-function"></a>Т. Обновление данных в удаленной таблице с помощью функции OPENQUERY  
 В следующем примере обновляется строка в удаленной таблице, указав [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) функцию набора строк. В этом примере используется имя связанного сервера, созданного в предыдущем примере.  
  
```sql  
UPDATE OPENQUERY (MyLinkServer, 'SELECT GroupName FROM HumanResources.Department WHERE DepartmentID = 4')   
SET GroupName = 'Sales and Marketing';  
```  
  
#### <a name="q-updating-data-in-a-remote-table-by-using-the-opendatasource-function"></a>У. Обновление данных в удаленной таблице с помощью функции OPENDATASOURCE  
 Следующий пример вставляет строку в удаленную таблицу, указав [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) функцию набора строк. Укажите допустимое имя сервера для источника данных, используя формат *имя_сервера* или *имя_сервера\имя_экземпляра*. Возможно, потребуется настроить у экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр Ad Hoc Distributed Queries. Дополнительные сведения см. в разделе [нерегламентированные распределенные запросы параметр конфигурации сервера](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md).  
  
```sql  
UPDATE OPENQUERY (MyLinkServer, 'SELECT GroupName FROM HumanResources.Department WHERE DepartmentID = 4')   
SET GroupName = 'Sales and Marketing';  
```  
  
###  <a name="LOBValues"></a>Обновление типов данных больших объектов  
 В примерах в этом разделе описываются методы обновления значений в столбцах, определенных с типами данных больших объектов (LOB).  
  
#### <a name="r-using-update-with-write-to-modify-data-in-an-nvarcharmax-column"></a>Ф. Использование инструкции UPDATE с предложением .WRITE для изменения данных в столбце nvarchar(max)  
 В следующем примере. Write для обновления частичного значения в `DocumentSummary`, **nvarchar(max)** столбца в `Production.Document` таблицы. Слово `components` заменяется словом `features` путем указания слова для замены, начального положения (смещения) заменяемого слова в существующих данных и количества заменяемых символов (длины). В примере также используется предложение OUTPUT для возврата до и после изображения `DocumentSummary` столбец `@MyTableVar` табличную переменную.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table (  
    SummaryBefore nvarchar(max),  
    SummaryAfter nvarchar(max));  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
OUTPUT deleted.DocumentSummary,   
       inserted.DocumentSummary   
    INTO @MyTableVar  
WHERE Title = N'Front Reflector Bracket Installation';  
SELECT SummaryBefore, SummaryAfter   
FROM @MyTableVar;  
GO  
```  
  
#### <a name="s-using-update-with-write-to-add-and-remove-data-in-an-nvarcharmax-column"></a>Х. Использование UPDATE с предложением .WRITE для добавления и удаления данных в столбце типа nvarchar(max)  
 В следующих примерах, добавления и удаления данных из **nvarchar(max)** столбца, имеющего значение в настоящее время равно NULL. Так как. СОЗДАВАТЬ предложения не может использоваться для изменения столбца значение NULL, а столбец сначала заполняется временными данными. Затем они заменяются правильными данными с помощью предложения .WRITE. В дополнительных примерах данные добавляются в конец значения столбца, удаляются из столбца (усекаются) и, наконец, удаляются частичные данные из столбца. Инструкции SELECT выводят на экран изменения данных, создаваемые каждой из инструкций UPDATE.  
  
```sql  
USE AdventureWorks2012;  
GO  
-- Replacing NULL value with temporary data.  
UPDATE Production.Document  
SET DocumentSummary = N'Replacing NULL value'  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Replacing temporary data with the correct data. Setting @Length to NULL   
-- truncates all existing data from the @Offset position.  
UPDATE Production.Document  
SET DocumentSummary .WRITE(N'Carefully inspect and maintain the tires and crank arms.',0,NULL)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Appending additional data to the end of the column by setting   
-- @Offset to NULL.  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N' Appending data to the end of the column.', NULL, 0)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Removing all data from @Offset to the end of the existing value by   
-- setting expression to NULL.   
UPDATE Production.Document  
SET DocumentSummary .WRITE (NULL, 56, 0)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Removing partial data beginning at position 9 and ending at   
-- position 21.  
UPDATE Production.Document  
SET DocumentSummary .WRITE ('',9, 12)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
```  
  
#### <a name="t-using-update-with-openrowset-to-modify-a-varbinarymax-column"></a>T. Использование инструкции UPDATE с функцией OPENROWSET для изменения столбца типа varbinary(max)  
 В следующем примере заменяется существующее изображение в **varbinary(max)** столбца заменяется новым изображением. [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) функция используется с параметром BULK для загрузки изображения в столбец. В этом примере предполагается, что по заданному пути существует файл с именем `Tires.jpg`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.ProductPhoto  
SET ThumbNailPhoto = (  
    SELECT *  
    FROM OPENROWSET(BULK 'c:Tires.jpg', SINGLE_BLOB) AS x )  
WHERE ProductPhotoID = 1;  
GO  
```  
  
#### <a name="u-using-update-to-modify-filestream-data"></a>Ф. Использование UPDATE для изменения данных FILESTREAM  
 В следующем примере инструкция UPDATE используется для изменения данных в файлах файловой системы. Не рекомендуется использовать этот метод для потоковой передачи больших объемов данных в файл. Используйте соответствующие интерфейсы Win32. В следующем примере любой текст в записи файла заменяется текстом `Xray 1`. Дополнительные сведения см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
```sql  
UPDATE Archive.dbo.Records  
SET [Chart] = CAST('Xray 1' as varbinary(max))  
WHERE [SerialNumber] = 2;  
```  
  
###  <a name="UDTs"></a>Обновление определяемых пользователем типов  
 В следующих примерах изменяются значения в столбцах определяемых пользователем типов данных CLR. Описываются три метода. Дополнительные сведения об определяемых пользователем столбцах см. в разделе [определяемые пользователем типы](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
#### <a name="v-using-a-system-data-type"></a>Х. Использование системных типов данных  
 Определяемый пользователем тип можно обновить путем предоставления значения в типе системных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при поддержке определяемым пользователем типа явного или неявного преобразования из этого типа. Следующий пример демонстрирует, как обновить значение в столбце определяемого пользователем типа `Point` путем явного преобразования строки.  
  
```sql  
UPDATE dbo.Cities  
SET Location = CONVERT(Point, '12.3:46.2')  
WHERE Name = 'Anchorage';  
```  
  
#### <a name="w-invoking-a-method"></a>ВТ. Вызов метода  
 Определяемый пользователем тип можно обновить путем вызова метода, отмеченного в качестве мутатора определяемого пользователем типа, для выполнения обновления. Следующий пример вызывает метод мутатора типа `Point` с именем `SetXY`. Это обновляет состояние экземпляра типа.  
  
```sql  
UPDATE dbo.Cities  
SET Location.SetXY(23.5, 23.5)  
WHERE Name = 'Anchorage';  
```  
  
#### <a name="x-modifying-the-value-of-a-property-or-data-member"></a>X. Изменение значения свойства или элемента данных  
 Определяемый пользователем тип можно обновить путем изменения значения зарегистрированного свойства или общедоступного элемента данных определяемого пользователем типа. Выражение, предоставляющее значение, должно допускать неявное преобразование в тип свойства. В следующем примере изменяется значение свойства `X` определяемого пользователем типа `Point`.  
  
```sql  
UPDATE dbo.Cities  
SET Location.X = 23.5  
WHERE Name = 'Anchorage';  
```  
  
###  <a name="TableHints"></a>Переопределение поведения по умолчанию оптимизатор запросов с помощью подсказок  
 Примеры в этом разделе описывают использование табличных подсказок и подсказок в запросах для временного переопределения поведения оптимизатора запросов при обработке инструкции UPDATE.  
  
> [!CAUTION]  
>  Поскольку оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно выбирает наилучший план выполнения запроса, подсказки рекомендуется использовать только опытным разработчикам и администраторам баз данных в качестве последнего средства.  
  
#### <a name="y-specifying-a-table-hint"></a>Y. Задание табличной подсказки  
 В следующем примере задается [табличную подсказку](../../t-sql/queries/hints-transact-sql-table.md) TABLOCK. Эта подсказка указывает, что на таблицу `Production.Product` накладывается совмещаемая блокировка, удерживаемая до завершения инструкции UPDATE.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.Product  
WITH (TABLOCK)  
SET ListPrice = ListPrice * 1.10  
WHERE ProductNumber LIKE 'BK-%';  
GO  
```  
  
#### <a name="z-specifying-a-query-hint"></a>Z. Задание подсказки в запросе  
 В следующем примере задается [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) `OPTIMIZE FOR (@variable)` в инструкции UPDATE. Эта подсказка указывает на необходимость использования оптимизатором запросов при компиляции и оптимизации запросов конкретного значения локальной переменной. Значение используется только в процессе оптимизации запроса, но не в процессе выполнения.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE PROCEDURE Production.uspProductUpdate  
@Product nvarchar(25)  
AS  
SET NOCOUNT ON;  
UPDATE Production.Product  
SET ListPrice = ListPrice * 1.10  
WHERE ProductNumber LIKE @Product  
OPTION (OPTIMIZE FOR (@Product = 'BK-%') );  
GO  
-- Execute the stored procedure   
EXEC Production.uspProductUpdate 'BK-%';  
```  
  
###  <a name="CaptureResults"></a>Сбор результатов инструкции UPDATE  
 Примеры в этом разделе демонстрируют, как использовать [предложение OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) для возврата сведений или на основе выражений, всех строк, изменившихся с помощью инструкции UPDATE. Эти результаты могут быть возвращены приложению, например для вывода подтверждающих сообщений, архивирования и т. п.  
  
#### <a name="aa-using-update-with-the-output-clause"></a>AA. Использование инструкции UPDATE с предложением OUTPUT  
 В следующем примере значения в столбце `VacationHours` в первых 10 строках таблицы `Employee` уменьшаются до 25 % от исходных значений, а в столбец `ModifiedDate` заносится текущая дата. Предложение `OUTPUT` возвращает значение `VacationHours`, существующее до применения инструкции `UPDATE` в столбце `deleted.VacationHours`, и обновленное значение в столбце `inserted.VacationHours` к табличной переменной `@MyTableVar`.  
  
 Две следующие инструкции `SELECT` возвращают значения в табличную переменную `@MyTableVar`, а результаты операции обновления — в таблицу `Employee`. Дополнительные примеры использования предложения OUTPUT см. в разделе [предложение OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25,  
    ModifiedDate = GETDATE()   
OUTPUT inserted.BusinessEntityID,  
       deleted.VacationHours,  
       inserted.VacationHours,  
       inserted.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
###  <a name="Other"></a>Использование UPDATE в других инструкциях  
 В примерах в этом разделе описывается использование UPDATE в других инструкциях.  
  
#### <a name="ab-using-update-in-a-stored-procedure"></a>AB. Использование UPDATE в хранимой процедуре  
 В следующем примере инструкция UPDATE используется в хранимой процедуре. Процедура принимает один входной параметр `@NewHours` и один выходной параметр `@RowCount`. `@NewHours` Значение параметра используется в инструкции UPDATE для обновления столбца `VacationHours` в таблице `HumanResources.Employee`. Выходной параметр `@RowCount` используется для возврата значения числа задействованных строк в локальную переменную. Выражение CASE используется в предложении SET для условного определения значения, которое задано для столбца `VacationHours`. Если для сотрудника применяется почасовая ставка оплаты (`SalariedFlag` = 0), то в столбце `VacationHours` устанавливается текущее количество часов плюс значение, заданное в `@NewHours`. В противном случае в столбце `VacationHours` указывается значение, заданное в `@NewHours`.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE PROCEDURE HumanResources.Update_VacationHours  
@NewHours smallint  
AS   
SET NOCOUNT ON;  
UPDATE HumanResources.Employee  
SET VacationHours =   
    ( CASE  
         WHEN SalariedFlag = 0 THEN VacationHours + @NewHours  
         ELSE @NewHours  
       END  
    )  
WHERE CurrentFlag = 1;  
GO  
  
EXEC HumanResources.Update_VacationHours 40;  
```  
  
#### <a name="ac-using-update-in-a-trycatch-block"></a>ПЕРЕМЕННОГО ТОКА. Использование UPDATE в блоке TRY…CATCH  
 В следующем примере инструкция UPDATE используется в блок TRY... CATCH для обработки ошибок выполнения, которые могут возникнуть во время операции обновления.  
  
```sql  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
  
BEGIN TRY  
    -- Intentionally generate a constraint violation error.  
    UPDATE HumanResources.Department  
    SET Name = N'MyNewName'  
    WHERE DepartmentID BETWEEN 1 AND 2;  
END TRY  
BEGIN CATCH  
    SELECT   
         ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
  
    IF @@TRANCOUNT > 0  
        ROLLBACK TRANSACTION;  
END CATCH;  
  
IF @@TRANCOUNT > 0  
    COMMIT TRANSACTION;  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="ad-using-a-simple-update-statement"></a>AD. Использование простой инструкции UPDATE  
 Следующие примеры как могут быть обработаны все строки при предложение WHERE не используется для указания строк (или строки) для обновления.  
  
 В этом примере обновляет значения в `EndDate` и `CurrentFlag` для всех строк в `DimEmployee` таблицы.  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimEmployee  
SET EndDate = '2010-12-31', CurrentFlag='False';  
```  
  
 В инструкции UPDATE можно также использовать вычисляемые значения. В следующем примере удваивается значение столбца `ListPrice` для всех строк в таблице `Product`.  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimEmployee  
SET BaseRate = BaseRate * 2;  
```  
  
### <a name="ae-using-the-update-statement-with-a-where-clause"></a>ФУНКЦИЯ ALWAYS ENCRYPTED. Использование инструкции UPDATE с предложением WHERE  
 В следующем примере предложение WHERE используется для указания строк, которые необходимо обновить.  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimEmployee  
SET FirstName = 'Gail'  
WHERE EmployeeKey = 500;  
```  
  
### <a name="af-using-the-update-statement-with-label"></a>AF. Использование инструкции UPDATE с меткой  
 Следующий пример показывает использование МЕТКУ для инструкции UPDATE.  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimProduct  
SET ProductSubcategoryKey = 2   
WHERE ProductKey = 313  
OPTION (LABEL = N'label1');  
```  
  
### <a name="ag-using-the-update-statement-with-information-from-another-table"></a>ГРУППЫ ДОСТУПНОСТИ. Использование инструкции UPDATE с данными из другой таблицы  
 Этот пример создает таблицу для хранения общего объема продаж по годам. Обновляет общий объем продаж за 2004 год, выполнив инструкцию SELECT для таблицы FactInternetSales.  
  
```sql  
-- Uses AdventureWorks  
  
CREATE TABLE YearlyTotalSales (  
    YearlySalesAmount money NOT NULL,  
    Year smallint NOT NULL )  
WITH ( DISTRIBUTION = REPLICATE );  
  
INSERT INTO YearlyTotalSales VALUES (0, 2004);  
INSERT INTO YearlyTotalSales VALUES (0, 2005);  
INSERT INTO YearlyTotalSales VALUES (0, 2006);  
  
UPDATE YearlyTotalSales  
SET YearlySalesAmount=  
(SELECT SUM(SalesAmount) FROM FactInternetSales WHERE OrderDateKey >=20040000 AND OrderDateKey < 20050000)  
WHERE Year=2004;  
  
SELECT * FROM YearlyTotalSales;   
```  

### <a name="ah-ansi-join-replacement-for-update-statements"></a>AH. Замена соединения ANSI для инструкций update
Вы можете обнаружить, что у вас есть сложные обновление, которое соединяет более двух таблиц, объединенных с помощью присоединения синтаксис ANSI для выполнения инструкции UPDATE или DELETE.  

Представьте, что было необходимо обновить в этой таблице:  

```sql
CREATE TABLE [dbo].[AnnualCategorySales]
(   [EnglishProductCategoryName]    NVARCHAR(50)    NOT NULL
,   [CalendarYear]                  SMALLINT        NOT NULL
,   [TotalSalesAmount]              MONEY           NOT NULL
)
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
;  
```

Исходный запрос может выглядел примерно так:  

```
UPDATE  acs
SET     [TotalSalesAmount] = [fis].[TotalSalesAmount]
FROM    [dbo].[AnnualCategorySales]     AS acs
JOIN    (
        SELECT  [EnglishProductCategoryName]
        ,       [CalendarYear]
        ,       SUM([SalesAmount])              AS [TotalSalesAmount]
        FROM    [dbo].[FactInternetSales]       AS s
        JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
        JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
        JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
        JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
        WHERE   [CalendarYear] = 2004
        GROUP BY
                [EnglishProductCategoryName]
        ,       [CalendarYear]
        ) AS fis
ON  [acs].[EnglishProductCategoryName]  = [fis].[EnglishProductCategoryName]
AND [acs].[CalendarYear]                = [fis].[CalendarYear]
;  
```

Поскольку [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] не поддерживает соединения ANSI в предложении FROM инструкции UPDATE, не удается скопировать этот код через без изменения ее слегка.  

Сочетание CTAS и неявное соединение можно использовать для замены этого кода:  

```sql
-- Create an interim table
CREATE TABLE CTAS_acs
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT  ISNULL(CAST([EnglishProductCategoryName] AS NVARCHAR(50)),0)    AS [EnglishProductCategoryName]
,       ISNULL(CAST([CalendarYear] AS SMALLINT),0)                      AS [CalendarYear]
,       ISNULL(CAST(SUM([SalesAmount]) AS MONEY),0)                     AS [TotalSalesAmount]
FROM    [dbo].[FactInternetSales]       AS s
JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
WHERE   [CalendarYear] = 2004
GROUP BY
        [EnglishProductCategoryName]
,       [CalendarYear]
;

-- Use an implicit join to perform the update
UPDATE  AnnualCategorySales
SET     AnnualCategorySales.TotalSalesAmount = CTAS_ACS.TotalSalesAmount
FROM    CTAS_acs
WHERE   CTAS_acs.[EnglishProductCategoryName] = AnnualCategorySales.[EnglishProductCategoryName]
AND     CTAS_acs.[CalendarYear]               = AnnualCategorySales.[CalendarYear]
;

--Drop the interim table
DROP TABLE CTAS_acs
;
```
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Курсоры (Transact-SQL)](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [Текст и изображения функции &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [С общее_табличное_выражение &#40; Transact-SQL &#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md)   
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
  
  
